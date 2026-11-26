# Prompt Engineering Mastery

## 1. Introduction

Prompt engineering is the process of designing and refining instructions given to Large Language Models (LLMs) to obtain accurate, consistent and useful responses.

The objective of this project is to explore three important prompt engineering techniques:

1. Zero-shot and Few-shot Prompting
2. Chain-of-Thought Prompting
3. Structured Output Generation using JSON

The experiments were conducted using Google AI Studio with a Gemini model. The same model was used throughout the experiments to maintain consistency.

The project focuses on comparing different prompting approaches, examining actual model outputs and understanding how prompt design influences LLM behaviour.

## 2. Tools and Technologies Used

- Google AI Studio
- Google Gemini
- Prompt Engineering
- Natural Language Processing concepts
- JSON (JavaScript Object Notation)

No programming code was required for conducting the experiments. All prompts were executed directly through the Google AI Studio interface.

Note: The exact Gemini model version was not recorded during the experiments.

---

# 3. Experiment 1: Zero-shot vs Few-shot Prompting

## 3.1 Objective

The objective was to compare the performance of zero-shot and few-shot prompting for sentiment classification of product reviews.

Sentiment classification involves identifying whether a given text expresses a positive, negative or neutral opinion.

Five product reviews were selected for testing.

## 3.2 Zero-shot Prompting

### Concept

Zero-shot prompting refers to asking an LLM to perform a task without providing any examples. The model relies on its existing knowledge and the instructions in the prompt.

### Actual Prompt Used

You are a sentiment classification system.

Classify each product review into one of these three categories:
- Positive
- Negative
- Neutral

Return the result in a numbered list. Give only the sentiment category for each review, without explanations.

Product reviews:

1. "The battery life is excellent and the phone works perfectly."
2. "The delivery was late and the product arrived damaged."
3. "The product is okay, nothing special."
4. "Amazing quality! I am extremely happy with this purchase."
5. "The headphones stopped working after just two days."

### Actual Model Output

1. Positive
2. Negative
3. Neutral
4. Positive
5. Negative

### Results

| Review | Expected Sentiment | Model Output |
|---|---|---|
| 1 | Positive | Positive |
| 2 | Negative | Negative |
| 3 | Neutral | Neutral |
| 4 | Positive | Positive |
| 5 | Negative | Negative |

Correct predictions: 5/5

Accuracy: 100%

## 3.3 Few-shot Prompting

### Concept

Few-shot prompting involves providing a small number of input-output examples in the prompt before asking the model to perform the actual task.

These examples demonstrate the expected pattern and help guide the model's responses.

### Actual Prompt Used

You are a sentiment classification system.

Classify product reviews into one of these three categories:
- Positive
- Negative
- Neutral

Follow the examples below to understand the expected classification.

Examples:

Review: "This laptop is fantastic. It runs smoothly and has excellent performance."
Sentiment: Positive

Review: "The product broke within a week. Very disappointed with the quality."
Sentiment: Negative

Review: "The package arrived today. It contains the item I ordered."
Sentiment: Neutral

Review: "Absolutely love this product! It exceeded all my expectations."
Sentiment: Positive

Now classify the following five reviews.

Return the results in a numbered list. Give only the sentiment category without explanations.

Reviews:

1. "The battery life is excellent and the phone works perfectly."
2. "The delivery was late and the product arrived damaged."
3. "The product is okay, nothing special."
4. "Amazing quality! I am extremely happy with this purchase."
5. "The headphones stopped working after just two days."

### Actual Model Output

1. Positive
2. Negative
3. Neutral
4. Positive
5. Negative

### Results

Correct predictions: 5/5

Accuracy: 100%

## 3.4 Comparison and Analysis

| Evaluation Metric | Zero-shot | Few-shot |
|---|---:|---:|
| Examples provided | 0 | 4 |
| Total test reviews | 5 | 5 |
| Correct predictions | 5 | 5 |
| Accuracy | 100% | 100% |

### Analysis

Both zero-shot and few-shot prompting successfully classified all five product reviews.

Zero-shot prompting performed well without requiring any demonstrations. Few-shot prompting provided additional guidance through four examples, demonstrating how the model should classify different types of reviews.

However, few-shot prompting did not improve the accuracy in this particular experiment because zero-shot prompting had already achieved 100% accuracy.

This experiment demonstrates that providing examples can guide model behaviour, although examples do not necessarily improve performance when the original instructions are already sufficient.

---

# 4. Experiment 2: Chain-of-Thought Prompting

## 4.1 Objective

The objective was to compare direct prompting with step-by-step prompting using a multi-step mathematical word problem.

The experiment examined whether explicitly requesting intermediate calculations would improve the transparency and reliability of the model's answer.

## 4.2 Mathematical Problem

A shopkeeper buys 40 notebooks at ₹25 each. He sells 30 notebooks at ₹35 each and the remaining 10 notebooks at ₹20 each.

What is his total profit or loss?

## 4.3 Direct Prompting

### Actual Prompt Used

Solve the following mathematical word problem and provide only the final answer. Do not include explanations or calculations.

A shopkeeper buys 40 notebooks at ₹25 each. He sells 30 notebooks at ₹35 each and the remaining 10 notebooks at ₹20 each.

What is his total profit or loss?

### Actual Model Output

Profit of ₹250

### Verification

Cost price = 40 × 25 = ₹1,000

Revenue from 30 notebooks = 30 × 35 = ₹1,050

Revenue from 10 notebooks = 10 × 20 = ₹200

Total revenue = ₹1,050 + ₹200 = ₹1,250

Profit = ₹1,250 - ₹1,000 = ₹250

The direct prompt generated the correct final answer.

## 4.4 Step-by-Step Prompting

### Concept

Chain-of-Thought prompting encourages a model to provide intermediate reasoning steps before presenting its final answer.

This technique can make multi-step problem solving easier to inspect and verify.

### Actual Prompt Used

Solve the following mathematical word problem.

Work through the problem step by step. Show the calculations for:

1. Total cost price.
2. Revenue from the first 30 notebooks.
3. Revenue from the remaining 10 notebooks.
4. Total revenue.
5. Final profit or loss.

Clearly state the final answer.

Problem:

A shopkeeper buys 40 notebooks at ₹25 each. He sells 30 notebooks at ₹35 each and the remaining 10 notebooks at ₹20 each.

What is his total profit or loss?

### Actual Model Output

Here is the step-by-step solution to the problem:

1. Total Cost Price

The shopkeeper buys 40 notebooks at ₹25 each.

Total Cost Price = 40 × ₹25 = ₹1,000

2. Revenue from the First 30 Notebooks

He sells 30 notebooks at ₹35 each.

Revenue from first 30 notebooks = 30 × ₹35 = ₹1,050

3. Revenue from the Remaining 10 Notebooks

He sells the remaining 10 notebooks at ₹20 each.

Revenue from remaining 10 notebooks = 10 × ₹20 = ₹200

4. Total Revenue

Add the revenue from both sets of notebooks.

Total Revenue = ₹1,050 + ₹200 = ₹1,250

5. Final Profit or Loss

Since the Total Revenue (₹1,250) is greater than the Total Cost Price (₹1,000), the shopkeeper makes a profit.

Profit = Total Revenue − Total Cost Price

Profit = ₹1,250 − ₹1,000 = ₹250

Final Answer:

The shopkeeper makes a total profit of ₹250.

## 4.5 Comparison and Analysis

| Evaluation Metric | Direct Prompt | Step-by-Step Prompt |
|---|---|---|
| Correct final answer | Yes | Yes |
| Final profit | ₹250 | ₹250 |
| Intermediate calculations | No | Yes |
| Explanation | No | Detailed |
| Accuracy | Correct | Correct |

### Analysis

Both prompting approaches produced the correct answer of ₹250 profit.

The direct prompt generated only the final result, whereas the step-by-step prompt provided calculations for the cost price, individual revenues, total revenue and final profit.

The step-by-step approach improved the transparency and interpretability of the response, allowing the calculations to be checked individually.

However, it did not improve final-answer accuracy in this experiment because the direct prompt had already produced the correct result.

This demonstrates that Chain-of-Thought prompting can be particularly useful when a task requires multiple calculations or intermediate steps, even when it does not necessarily improve accuracy in every case.

---

# 5. Experiment 3: Structured Output Generation Using JSON

## 5.1 Objective

The objective was to evaluate whether an LLM could consistently extract specific information from unstructured text and return it in a predefined JSON format.

Five different text inputs were tested.

The required information included:

- Name
- Date
- Amount
- Payment method

The experiment also examined how the model handled missing information and different date and currency formats.

## 5.2 JSON Schema and Prompt Design

### Required JSON Structure

{
  "name": "string",
  "date": "YYYY-MM-DD",
  "amount": 0,
  "payment_method": "string"
}

The following rules were specified:

1. Use exactly four keys: name, date, amount and payment_method.
2. Name must be a string.
3. Date must follow YYYY-MM-DD format.
4. Amount must be a number without currency symbols.
5. Payment_method must be a string.
6. If information is missing, use null.
7. Return valid JSON only, without explanations or Markdown formatting.

An example output was also provided to demonstrate the expected format.

### Prompt Used

You are an information extraction system.

Extract the following information from the given text:

- name
- date
- amount
- payment_method

Return the extracted information in valid JSON only.

Follow these rules:

1. Use exactly these four keys: "name", "date", "amount", and "payment_method".
2. Name must be a string.
3. Date must be in YYYY-MM-DD format.
4. Amount must be a number without currency symbols.
5. Payment_method must be a string.
6. If any information is missing, use null.
7. Do not include explanations, markdown formatting, or text outside the JSON object.

Example output:

{
  "name": "John",
  "date": "2026-01-15",
  "amount": 2500,
  "payment_method": "Credit Card"
}

## 5.3 Test Inputs and Actual Outputs

### Test 1: Complete Transaction Information

Input:

"Yesterday, Sarah Johnson purchased groceries worth Rs. 1,250 using UPI. The transaction took place on 25 November 2026."

Actual Model Output:

{
  "name": "Sarah Johnson",
  "date": "2026-11-25",
  "amount": 1250,
  "payment_method": "UPI"
}

Result: Passed

### Test 2: Missing Payment Method

Input:

"On 18 October 2026, Michael Brown made a payment of Rs. 3,500 for his online course. The transaction was completed successfully."

Actual Model Output:

{
  "name": "Michael Brown",
  "date": "2026-10-18",
  "amount": 3500,
  "payment_method": null
}

Result: Passed

### Test 3: Different Currency and Payment Format

Input:

"Priya Sharma paid INR 8,750 through her Visa debit card on 5 November 2026 for a laptop purchase."

Actual Model Output:

{
  "name": "Priya Sharma",
  "date": "2026-11-05",
  "amount": 8750,
  "payment_method": "Visa debit card"
}

Result: Passed

### Test 4: Different Text Structure and Decimal Amount

Input:

"Your transaction confirmation: A payment of Rs. 499.50 was made using Google Pay by customer Ananya Menon on 12/11/2026."

Actual Model Output:

{
  "name": "Ananya Menon",
  "date": "2026-11-12",
  "amount": 499.5,
  "payment_method": "Google Pay"
}

Result: Passed

Note: The numeric values 499.50 and 499.5 are equivalent. JSON numbers do not preserve insignificant trailing zeros.

### Test 5: Missing Date and Different Payment Method

Input:

"Customer Rahul Nair paid Rs. 2,000 for a software subscription using net banking."

Actual Model Output:

{
  "name": "Rahul Nair",
  "date": null,
  "amount": 2000,
  "payment_method": "net banking"
}

Result: Passed

## 5.4 Structured Output Results

| Test | Name | Date | Amount | Payment Method | Result |
|---|---|---|---|---|---|
| 1 | Correct | Correct | Correct | Correct | Pass |
| 2 | Correct | Correct | Correct | Null handled | Pass |
| 3 | Correct | Correct | Correct | Correct | Pass |
| 4 | Correct | Correct | Correct | Correct | Pass |
| 5 | Correct | Null handled | Correct | Correct | Pass |

Total test inputs: 5

Successful outputs: 5

Success rate: (5/5) × 100 = 100%

## 5.5 Analysis

The model successfully extracted all the required information from five different text inputs.

The explicit JSON schema and clearly defined instructions helped maintain a consistent output structure.

The use of examples demonstrated the expected JSON format, while the instruction to represent missing information using null prevented the model from needing to invent unavailable values.

The model also successfully handled different currency representations, decimal amounts, date formats and missing fields.

All five outputs were visually checked against the required keys, values and data types. However, automated JSON parsing and schema validation were not performed.

The experiment demonstrates that explicit instructions, predefined schemas and examples can improve the consistency of structured LLM outputs.

Note: The experiment used prompt-based JSON generation in Google AI Studio. A dedicated JSON mode or structured-output API feature was not tested.

---

# 6. Overall Results and Comparison

The three experiments demonstrated different aspects of prompt engineering.

| Experiment | Technique | Result |
|---|---|---|
| 1 | Zero-shot | 5/5 correct |
| 1 | Few-shot | 5/5 correct |
| 2 | Direct prompting | Correct |
| 2 | Step-by-step prompting | Correct |
| 3 | Structured JSON | 5/5 passed |

### Key Observations

1. Zero-shot prompting was sufficient for straightforward sentiment classification.
2. Few-shot prompting provided examples that demonstrated the expected classification pattern.
3. Step-by-step prompting improved the transparency of mathematical problem solving.
4. Explicit JSON formatting instructions helped produce consistent structured outputs.
5. The use of null values allowed the model to represent missing information appropriately.

---

# 7. Challenges and Limitations

Although the experiments produced successful results, some limitations should be considered.

- The sentiment classification experiment used only five reviews, which is a relatively small dataset.
- Both zero-shot and few-shot prompting achieved the same accuracy, so a larger and more challenging dataset would be needed to determine whether few-shot prompting provides a measurable improvement.
- The mathematical experiment used one problem, which is insufficient to establish that step-by-step prompting always improves reasoning accuracy.
- The structured output experiment used five inputs and was evaluated manually rather than through an automated JSON validator.
- The exact Gemini model version was not recorded, which limits reproducibility.

Future experiments could include larger datasets, more complex reasoning tasks and automated JSON schema validation.

---

# 8. Conclusion

This project provided practical experience with three important prompt engineering techniques: zero-shot and few-shot prompting, Chain-of-Thought prompting and structured output generation.

The experiments demonstrated that the way instructions and examples are presented to an LLM can influence the format, consistency and transparency of its responses.

Zero-shot and few-shot prompting both achieved 100% accuracy in the sentiment classification task. Step-by-step prompting produced a more detailed and verifiable mathematical solution, while structured output prompting successfully extracted transaction information into the required JSON format across all five test inputs.

Overall, the project highlighted the importance of clear instructions, examples, predefined output formats and systematic evaluation when working with Large Language Models.

Prompt engineering is an important skill for developing reliable AI applications, particularly in tasks involving information extraction, classification, reasoning and structured data generation.

**Project Status: Completed**
