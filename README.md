# Entropy guided Unspervised domain adaptation
This project is an implementation of the research paper: <a href="https://www.researchgate.net/publication/345238526_Entropy_Guided_Unsupervised_Domain_Adaptation_for_Cross-Center_Hip_Cartilage_Segmentation_from_MRI">Entropy Guided Unsupervised Domain Adaptation for Cross-Center Hip Cartilage Segmentation from MRI.</a> The authors of this paper have not released the source code.
We make two essential changes:
<li>We replace the orignal segmentation backbone with a U-Net for reasons described in our report.</li>
<li>Our target dataset (<a href="https://sites.google.com/view/calgary-campinas-dataset/home">CC-359</a>) is different from the orignal paper.</li>

## Snapshot of our results:



## Tasks performed:
<ul>
  <li>Implement from scratch, the architecture and adversarial training methodology as described in the 
<a href="https://www.researchgate.net/publication/345238526_Entropy_Guided_Unsupervised_Domain_Adaptation_for_Cross-Center_Hip_Cartilage_Segmentation_from_MRI">orginal paper</a> (code was not released by authors)</li>
  <li>Data preprocessing for efficient pytorch dataloaders.</li>
  <li>Progressively train and test individual components of the network (i.e. the segmenter and discriminator networks).</li>
  <li>Hyperparameter optimization for adversarial domain adaptation</li>
</ul>


## Abstract
Image segmentation is an important part of most medical applications ranging from diagnostics to medicine research. Deep learning based segmentation suffers from the problem of domain shift. A segmentation model trained on
scans from a particular center or device (source domain) performs poorly when used for a novel center or device (target
domain). To that end, in this lab, we implement a paper for Entropy guided domain adaptation by Zeng et. al. that introduces
an adversarial learning based domain invariant segmentation model. The proposed model consists of a segmenter that is
trained in a supervised manner to segment scans from the source domain. Additionally, the model contains two auxiliary
discriminator networks, that discriminate between the segmenter features maps and the output entropy maps respectively, for
the source and target domain. They propose using these discriminators to adversarially train the segmenter to produce domain
invariant features maps and low entropy predictions. DICE Score and Surface Dice score were used to evaluate the segmentation
performance and corresponding domain shift. In this work, we show a successful implementation of the original paper with a
few crucial changes. Unlike the original paper, we use the U-Net architecture for segmentation. We also use a different dataset
(Calgary Campinas Brain MRI data). In addition, we contribute to this work by experimenting with some other approaches. We
investigate the effect of training the feature discriminator on both the source and target domains, unlike the original paper. We
also show results with the addition of direct entropy minimization. Moreover, for comparison, we also produce results by jointly
training the entire network from scratch, instead of fine-tuning the segmenter, as suggested in the original paper. In general, we
present various successful domain adaptation methods, especially when the domain shift is high.<br>
**Keywords:** Unsupervised Domain Adaptation, Segmentation, Brain MRI

## General Pre-requisites:
- Access to the Calgary Campinas CC-359 dataset (https://sites.google.com/view/calgary-campinas-dataset/home)
- Deep mind libray for surface distance (https://github.com/deepmind/surface-distance)
- Deep-pipe library (https://deep-pipe.readthedocs.io/en/latest/)

## Guide to run on Google Colab

### View the code at:
 - Implementation of original model : https://colab.research.google.com/drive/1i8NZjhn-xSChntrxJ-H3UJQwlD2oMo4B?usp=sharing
 - Modified implementation to run other experiments: https://colab.research.google.com/drive/1B7T-Fncv7GOjojs39WIO8xT_0_Ddu3Tu?usp=sharing (Similar to code above with minor modifications)
 - Pre-training the segmenter: https://colab.research.google.com/drive/1LdEZWETB3oq-9l4Ha5RTlmZNER0UhHtB?usp=sharing

### Pre-requisites to run
 1. To run the notebooks as is you will need a pro account. Otherwise you will have to make changes to the Dataset based on available memory.
 2. After downloading the CC359 dataset you can upload the scans to your google drive with the folder structure mentioned below:

  - The folder structure used for running this notebook is: 
    - base_path = '/content/gdrive/MyDrive/VMIA_Lab_Data/data/'
    - original_path = base_path + 'Original/Original/'
    - mask_path = base_path + 'Silver-standard-machine-learning/Silver-standard/'

3. Adapt your folder structure accordingly. Alternatively make changes to the paths in the Dataset class of the code.
4. All other instructions and pointers are also provided in the code files.
