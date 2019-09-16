# COCO-Assistant<img src="rep_stuff/coco.png" height="40">

Helper for dealing with MS-COCO annotations. 

## Overview
The MS COCO annotation format along with the pycocotools library is quite popular among the computer vision community. Yet I for one found it difficult to play around with the annotations. Deleting a specific category, combining multiple mini datasets to generate a larger dataset, viewing distribution of classes in the annotation file are things I would like to do without writing a separate script for each. The COCO Assistant is designed (or being designed) to assist with this exact problem.

### Requirements
Your data directory should look as follows:

```
Example:
.
├── images
│   ├── train
│   ├── val
|   ├── test
|   
├── annotations
│   ├── train.json
│   ├── val.json
│   ├── test.json

``` 

## Installation

```
# Clone the repository
git clone https://github.com/ashnair1/COCO-Assistant.git
# Build and install the library
make
```

## Usage

Usage is identical to how you would use `pycocotools`

```
from coco_assistant.coco_assistant import COCO_Assistant

# Specify image and annotation directories
img_dir = os.path.join(os.getcwd(), 'images')
ann_dir = os.path.join(os.getcwd(), 'annotations')

# Create COCO_Assistant object
cas = COCO_Assistant(img_dir, ann_dir)
```
## So what can CASS do?:

#### Merge datasets

The `combine` function allows you to merge  multiple datasets.

#### Remove_cat

Removes a specific category from an annotation file.

#### Generate annotation statistics

1. Generate countplot of instances per category that occur in the annotation files.
2. Generate pie-chart that shows distribution of objects according to their size (as specified in areaRng).

#### Visualise annotations

Couldn't `pycocotools` visualise annotations (via [showAnns](https://github.com/cocodataset/cocoapi/blob/636becdc73d54283b3aac6d4ec363cffbb6f9b20/PythonAPI/pycocotools/coco.py#L233)) as well? Sure it could, but I required a way to freely view all the annotations of a particular dataset so here we are.

![](./rep_stuff/visualiser.gif)

### In Progress: 
#### COCO to YOLO Converter

Converts COCO annotations to YOLO format (modified version of ultralytics's [original repo](https://github.com/ultralytics/COCO2YOLO))
