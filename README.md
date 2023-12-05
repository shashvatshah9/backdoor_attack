# Backdoor Attack
## Requirements

You must do the project individually. In this HW you will design a backdoor detector for
BadNets trained on the YouTube Face dataset using the pruning defense discussed in
class. Your detector will take as input:
1. B , a backdoored neural network classifier with N classes.
2. Dvalid , a validation dataset of clean, labelled images.

What you must output is G a “repaired” BadNet. G has N+1 classes, and given unseen test
input, it must
1.  Output the correct class if the test input is clean. The correct class will be in [1,N].
2. Output class N+1 if the input is backdoored.
   
You will design G using the pruning defense that we discussed in class. That is, you will prune
the last pooling layer of BadNet B (the layer just before the FC layers) by removing one
channel at a time from that layer. Channels should be removed in decreasing order of average
activation values over the entire validation set. Every time you prune a channel, you will
measure the new validation accuracy of the new pruned badnet. You will stop pruning once the
validation accuracy drops atleast X% below the original accuracy. This will be your new
network B'.
Now, your goodnet G works as follows. For each test input, you will run it through both B and
B'. If the classification outputs are the same, i.e., class i, you will output class i. If they differ you
will output N+1. Evaluat this defense on:
1. A BadNet, B 1 , (“sunglasses backdoor”) on YouTube Face for which we have already
told you what the backdoor looks like. That is, we give you the validation data, and
also test data with examples of clean and backdoored inputs.

## The repo contains a jupyter notebook which bad_net.ipynb 
It contains all the code needed to replicate the experiment
