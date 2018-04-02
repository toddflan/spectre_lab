<p align="center">
 <img src="https://spectreattack.com/images/spectre.min.svg" width="200">
</p>

## Introduction

In early 2018, Spectre, a vulnerability affecting nearly all modern computer systems, was announced to the public. Unlike most vulnerabilities, Spectre takes advantage of the intended operation of machines. Specifically, Spectre exploits the side-effects of branch prediction and speculative execution, two invaluable architectural techniques, to gain secret information. These concepts will be explained in detail in the following sections.

## Purpose

The purpose of this lab is to gain a working understanding of the Spectre vulnerability, learn what parameters can increase the accuracy of the example code, and how the characteristics of the system affect Spectre’s performance.

## Branch Prediction and Speculative Execution

In modern processors, in order to keep up the increases of performance required to stay competitive, many tricks and techniques are used to increase the effective throughput of the processor without just increasing the processor speed or increasing the amount of instructions that can be issued at a time. Branch prediction for example allows the processor to try and guess if the branch will be taken or not to calculate the address offsets ahead of time making branch instructions less costly. An obvious example of where this can help is in a looping structure like a while, for, or do while loop. The condition will always be true until the loop terminates, so if a processor guesses that branch is always taken, it’s extremely likely to be correct. This is a somewhat naive example of branch prediction, but can be very effective. Modern processors use techniques like tournament predictors or perceptron predictors that are incredibly accurate.

The Spectre attack takes advantage of branch predictor behavior to trick the branch predictor to speculatively execute code by accident, and when it rolls back to go the other branch direction, there are side effects leftover than can be measured.

## Procedure

1.	Download an Ubuntu image and build a VM to run the attack code. There should be no extra libraries required outside of the LTS ubuntu image (16.04)

2.	Download the Spectre example code which can be downloaded [here](https://gist.github.com/ErikAugust/724d4a969fb2c6ae1bbd7b2a9e3d4bb6). This was produced as part of the Spectre paper which you can read [here](https://spectreattack.com/spectre.pdf).

3.  Compile and execute the example attack

    Run the command `gcc -o spectre spectre.c` then `./spectre` and examine the output. Make sure to compile without optimizations as this may cause issues running the attack code

4.	Edit spectre.c to output % confidence instead of success/unknown (line 134)

    Include your implementation of this feature with an explanation in your report.

5.	Edit the CACHE_HIT_THRESHOLD (line 50) and graph its effect on % confidence and correctness of the output.

6.	Edit the amount of times the branch predictor is trained between each malicious call to victim_function (line 76) and graph its effect on % confidence and correctness of the output.

## Deliverables

1.	Implementation of % confidence feature and explanation
2.	Graph of % confidence and success of the attack versus CACHE_HIT_THRESHOLD with analysis
3.	Graph of % confidence and success of the attack versus training iterations (for branch predictor) with analysis
5.	Demo code

## Authors

Eric Garfinkle, Gino Chacon, Samuel Todd Flanagan, Dr. Jeyavijayan Rajendran

## Credit

- Example Spectre attack code provided by Erik August's [Gist](https://gist.github.com/ErikAugust/724d4a969fb2c6ae1bbd7b2a9e3d4bb6)
- Information regarding Spectre attack found at [spectreattack.com](https://spectreattack.com/)
- Spectre logo [source](https://spectreattack.com/)
