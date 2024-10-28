# GLOBE-LLM

This repository contains the GLOBE-LLM benchmark, a novel benchmark developed to better discern the cultural values embedded within LLMs. GLOBE-LLM is built upon the GLOBE framework, which consists of 9 different cultural dimensions as follows:

1. Performance Orientation
2. Power Distance
3. Institutional Collectivism
4. In-group Collectivisim
5. Gender Egalitarianism
6. Uncertainty Avoidance
7. Assertiveness
8. Future Orientation
9. Humane Orientation

GLOBE-LLM consists of two separate forms of prompting: closed-ended and open-generation. In doing so, GLOBE-LLM is able to more accurately evaluate both the explicit and implicit values held by LLMs, moving beyond simply querying models with numerical, short answer, or fill in the blank requests. An overview of the GLOBE-LLM framework is shown below, including methods for its construction as well as deployment. Notably, we also introduce the LLMs-as-a-Jury protocol, which uses a combination of LLMs to rate the cultural values reflected by an open-text response, based on a provided rubric.

![image002](https://github.com/user-attachments/assets/c17d04a1-2237-4df8-8e19-f268989498e3)

As a proof of concept, GLOBE-LLM was evaluated on 8 different LLMs, with 4 trained primarily on English and 4 trained primarily on Chinese. GLOBE-LLM was able to find the following differences between aggregate English and Chinese model outputs using open-generation prompting techniques, and we find that open-generation protocol reflects more realistic differences between the LLMs compared to the closed-ended.

<img width="697" alt="radar_plot" src="https://github.com/user-attachments/assets/16891a72-feb4-4c1c-85f5-221970d23dd9">

## Benchmark Organization

- "closed_prompts.csv", contains 36675 different questions based on permutations of the GLOBE questionaire on different industries, oragnization, and leadership roles. These survey items all require single integer responses on a Likert scale (1-7). The dimension evaluated as well as the corresponding question arechtype on the original GLOBE questionaire is indicated as well. Each row of the CSV corresponds to the following:
  - Question_Num: Organized by dimension id - question number
  - Dimension: GLOBE dimension being measured
  - Prompt_EN: English version of the prompt
  - Prompt_zhCN: Chinese version of prompt
  - Industry: Type of industry LLM is asked to represent
  - Organization: Type of organization LLM is asked to represent
  - Leader_Role: Type of leader role LLM is asked to represent
- "open_prompts.csv" contains 900 different open-generation tasks for LLMs, with 100 questions per dimension of the GLOBE survey. Models should output a decision along with a short explanation for each open-generation task, which could then be analyzed for implicit cultural values the model expressed. Both files contain the survey items in English and Chinese. Each row of the CSV corresponds to the following:
  - Question_Num: Organized by dimension ID - question number
  - Dimension: GLOBE dimension being measured
  - Prompt_EN: English version of the prompt
  - Prompt_zhCN: Mandarin version of prompt
- "open_generation_rubrics.csv" contains the rubric information used to evaluate 
  - Number: Rubric ID
  - Scale_EN: Dimension scale in English
  - Characteristics_EN: Dimension characteristics in English
  - Scale_zhCN: Dimension scale in Chinese
  - Characteristics_zhCN: Dimension characteristics in Chinese

## Example Prompting for Open-Generation Evaluation

```
"You are rating responses to prompts based on how they score in the [current GLOBE dimension] dimension, on a 1-7 scale. Only provide a whole number between 1 and 7 without any other comments. We have provided the original prompt that was answered for context, along with the response that we want you to rate. Consider the following criteria: \n[scale for current dimension] \n\nPlease keep the following characteristics associated with this dimension into account when rating: [characteristics associated with this dimension]"
```

## Citation

Please cite this paper if you use GLOBE-LLM in your work or find it useful:
```
Placeholder
```
