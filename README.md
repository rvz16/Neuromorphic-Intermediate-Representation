# Neuromorphic Intermediate Representation

*Project for the Nature Inspired Computing (NIC) course based on the article [“Title”](https://www.nature.com/articles/s41467-024-52259-9).*

## Introduction

Spiking Neural Networks (SNNs) represent an advanced approach in neural computation, aiming to emulate the temporal dynamics and signaling mechanisms of biological neurons more accurately than traditional artificial neural networks (ANNs). Early neural models relied on simplified mathematical formulations; however, they were unable to capture the dynamic processes of neuronal communication fully. In biological systems, neurons communicate via chemical neurotransmitters across synapses, creating measurable membrane potentials that initiate neural activity.

SNNs leverage these biological principles by incorporating impulse amplitude and precise timing into their computations, thus enabling the simulation of recurrent neural behavior. A significant advantage of SNNs is their markedly reduced energy consumption compared to traditional ANNs.

## Goal of Study

The primary goal of this study is to develop a system that converts SNN structures between different deep learning libraries. Currently, there are seven major libraries used to construct spiking neural networks. In response to reproducibility challenges and the need for a unified representation, Jens E. Pedersen and colleagues developed a library called NIR (Neuromorphic Intermediate Representation).

In discussing the approach, Jens E. Pedersen stated:  
> "Creating a network and seeing how it learns in different libraries is actually a wonderful project! A significant problem in the field, as we point out in the paper, is reproducibility and establishing common understanding. With a single representation—such as NIR—we can reuse the model across various works, platforms, and hardware settings. More work is needed to understand how NIR graphs compare across libraries, so such studies are most welcome!" 

Accordingly, we compared different libraries to one another, and in the process, identified and reported several errors.

## How NIR Works

The NIR library accepts a neural network and a data sample as inputs and produces a graph that encapsulates key layer information—such as hyperparameters, weights, and encoding phases. Once the network is converted into this intermediate graph representation, it can be deployed across various deep learning libraries dedicated to spiking neural networks. Essentially, the Intermediate Representation serves as a flexible graph-based model conversion framework.

## Results

To elucidate the dynamics of spiking neural networks, we utilized a neuromorphic dataset and analyzed how the data is represented and processed within our network framework. Initially, we selected the Norse library—a deep learning library for SNNs—to construct a network aimed at solving a basic digit recognition problem. For this purpose, we used the NMNIST dataset, an enhanced version of MNIST that incorporates spike events and temporal sequences.

After training the network in Norse, we employed NIR to convert the network into a format compatible with another library, SnnTorch. During this conversion process, we encountered an issue: Norse does not currently support the conversion of MaxPooling layers. We reported this discrepancy, which led to the opening of an issue on the Norse GitHub repository [here](https://github.com/norse/norse/issues/418).

Subsequently, we developed a network using SnnTorch without MaxPooling layers to train on the NMNIST dataset. This model achieved an accuracy of *<placeholder>*. The next step involved converting this SnnTorch model into a graph format via NIR and importing it into Norse for a comparative analysis. We observed a discrepancy in time step recognition between the libraries due to differing discretization methods: SnnTorch and Norse each employ their own approach. After resolving these issues and refining the network training, we achieved an accuracy of *<placeholder>*.

