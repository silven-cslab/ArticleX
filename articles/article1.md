<h1 align="center"><em>Beyond LLMs: Structured Decision-Making Models, Jev, and Laya</em></h1>

----

## What if an AI model didn't need to generate text at all?

For example, if we want to categorize a complaint from a building into respective categories like ***Electrical***, ***Plumbing***, ***Maintenance***, etc.

These are different approaches for our example:

```json
Traditional LLM:

    Complaint → AI → "This looks like a high-priority electrical issue..."



Decision-Oriented Model:

    Complaint → AI → {

                            category : electrical,

                            priority : high,

                            confidence : 0.94

                        }

```

LLMs are primarily designed to generate language. But many applications don't actually need language; instead, they need **decisions, classifications, or probabilities that software can consume directly.**

----

## Structured, Probabilistic, Selective Decision Making

### Structured Prediction:

The process of predicting the labels of objects/data based on the information given about the relationships between the objects/data.

Example: **Computer Vision**

>             objects = pixels,
>
>             prediction = image segmentation. (predicts labels for every single pixel.)

### Probability Calibration:

During the classification of objects/data into labels, we may obtain probabilities that provide some confidence in the prediction.

Some models may provide poor estimates of the labels, and some may not support probability prediction at all.

Calibration allows us to better calibrate the probabilities of a model, or to add support for probability prediction.

### Decision Calibration:

This shifts the focus from traditional probability calibration to optimizing model outputs directly for downstream decision-making and loss minimization.

While probability prediction ensures that a model's predicted confidence scores match real-world outcomes, decision calibration guarantees that the predictions are reliable specifically for actions and decision-making.

### Selective Prediction:

Structured prediction is the task of predicting an output with a structured form, where multiple predicted values may have relationships or constraints between them.

Otherwise, the system holds back.

Example: For instance, a support system classifies incoming tickets as `billing`, `account`, or `technical`. The model returns the following prediction:

```json

        billing:   0.82

        account:   0.11

        technical: 0.07

```

But, a selective prediction adds another decision:

```json

        predicted class: billing

        selection score: 0.82

        threshold: 0.75

        result: accept prediction 

```

### Non-autoregressive (NAR) Generation:

Non-autoregressive (NAR) generation reduces or removes the sequential dependency found in conventional autoregressive generation, allowing multiple output elements to be generated or processed in parallel.

This can substantially reduce latency, which is particularly valuable for systems that need to make decisions at high throughput.

----

Based on the above topics, a new type of AI model was introduced specifically to make fast, structured, and probabilistic decisions for software applications.

## TypeSafe AI Jev:

TypeSafe describes Jev as a System One model, referring to a fast decision-making system designed to produce immediate structured judgments rather than lengthy reasoning traces.

The basic idea:

> Input → generated text → parsing → validation → software decision

- **Input Token Cost**: **$0.042 per million tokens (MTok)**

- **Output Token Cost**: **Free — TypeSafe describes them as “too cheap to meter”**

- **Latency**: Designed for ***sub-second responses***

#### What makes Jev different?

TypeSafe AI describes Jev as a **frontier-intelligence function call**: unstructured state goes in, and typed probabilistic decisions come out.

Currently, Jev supports three main question types:

* Choice → Select an option → **Choice + probabilities + confidence**

* Score → Evaluate something against a rubric → **Score + probabilities + confidence**

* Noul → Determine whether a statement is true/false → **Value from 0 - 1**

#### Calibrated Decisions:

One of Jev's central ideas is ***calibration***.

Instead of simply returning an answer, Jev provides an estimate of its uncertainty. The goal is that a higher confidence value should correspond to a higher likelihood of being correct. This allows developers to build systems such as:

>       High confidence → automate
>
>
>       Low confidence → send to human review

##### RLCD:

TypeSafe says Jev is trained based on ***Reinforcement Learning for Calibrated Decisions.***

In conventional LLM training, methods such as **RLHF** optimize for responses that humans prefer, while **RLVR** can optimize for outputs that are objectively verifiable. TypeSafe says **RLCD** instead focuses on calibrated decisions—the model should not only choose an answer, but also communicate how likely that answer is to be correct. In other words, ***higher confidence should correspond to higher actual accuracy***.

----

## ConvAI Innovations Laya:

Laya is an open-weight model from ****ConvAI Innovations**** that explores a similar design direction: **fast, non-autoregressive decision-making with structured outputs and uncertainty estimation**.

Laya is not simply a rebranding of Jev, but it supports **100+ languages through Laya's multilingual checkpoint**, with typical reported latency ***~32.8 ms for multilingual / ~39.5 ms English on a T4***.

----


AI is evolving beyond text generation toward fast, structured, and reliable decision-making.
Jev and Laya demonstrate this shift toward efficient, uncertainty-aware AI.


## References:

1. https://theory.stanford.edu/~tim/talks/bwca_statrec_public.pdf

2. https://scikit-learn.org/stable/modules/calibration.html

3. https://arxiv.org/abs/2107.05719

4. https://nalar.dev/let-classifiers-abstain-with-selective-prediction

5. https://arxiv.org/pdf/1711.02281

6. https://typesafe.ai

7. https://docs.typesafe.ai/introduction

8. https://typesafe.ai/blog/introducing-system-one-models-and-jev

9. https://huggingface.co/convaiinnovations/laya

10. https://github.com/NandhaKishorM/laya

11. https://laya.convaiinnovations.com


----
