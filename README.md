# TDS Virtual TA Project

## Overview

This project is a **Virtual Teaching Assistant (TA)** designed for the TDS (Tools for Data Science) course. It leverages AI to answer student queries, clarify doubts, and provide relevant resources using a custom API endpoint. The project is structured to allow easy evaluation and benchmarking of the AI’s responses using [Promptfoo](https://github.com/promptfoo/promptfoo).

## Features

- **Custom API Integration:** Easily connect your own AI model or proxy endpoint.
- **Automated Evaluation:** Use Promptfoo to run and score multiple test cases.
- **Flexible Test Design:** Add or modify questions, assertions, and evaluation rubrics in YAML.
- **Supports Attachments:** Reference images or links in test cases for richer context.

## File Structure

- `project-tds-virtual-ta-promptfoo.yaml`  
  Main configuration file for Promptfoo, containing provider setup, test cases, and assertions.
- `project-tds-virtual-ta-q1.webp`  
  Example image file referenced in a test case.
- `README.md`  
  This documentation file.

## How It Works

1. **API Provider:**  
   The YAML config defines a provider (your API endpoint) that receives questions and returns answers.

2. **Test Cases:**  
   Each test in the YAML file specifies a question (and optionally an image or link) to send to the API.

3. **Assertions:**  
   Responses are checked using assertions (e.g., `llm-rubric`, `contains`, `is-json`) to ensure quality and correctness.

4. **Evaluation:**  
   Run all tests and view results using Promptfoo’s CLI.

## Getting Started

### 1. Install Dependencies

Install [Promptfoo](https://github.com/promptfoo/promptfoo):

```bash
npm install -g promptfoo
# or, for one-off runs:
npx -y promptfoo eval --config project-tds-virtual-ta-promptfoo.yaml
```

### 2. Configure Your API

Edit the `providers` section in `project-tds-virtual-ta-promptfoo.yaml` to point to your API endpoint.

### 3. Add Test Cases

Modify or add new tests under the `tests:` section in the YAML file.

### 4. Run Evaluation

```bash
promptfoo eval --config project-tds-virtual-ta-promptfoo.yaml
```

### 5. Review Results

Check the output in your terminal or in the generated results file.

## Example Test Case

````yaml
- vars:
    question: "When is the TDS Sep 2025 end-term exam?"
  assert:
    - type: llm-rubric
````
