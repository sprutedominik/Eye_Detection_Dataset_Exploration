# Eye Detection Dataset Exploration

A Kaggle notebook that checks whether a public eye detection dataset is clean enough to train a detector on. No model is trained here.

## Why

Before training an object detector, I want to know what the labels look like. Are the boxes on the eyes? How large are they? A detector trained on misaligned boxes learns the wrong thing, and it is much cheaper to find that out by plotting than by training.

## What the notebook does

1. Walks the dataset folders (`train`, `val`, `test`, each with `images` and `labels`).
2. Counts the training images: 1,385.
3. Opens one YOLO label file and explains the format: `class x_center y_center width height`, all relative to image size.
4. Converts the relative values to pixels and draws the box on the image with OpenCV and Matplotlib.
5. Draws boxes on six random training images in a grid.
6. Plots histograms of box width and height across the training labels.

The plots are saved in the notebook output, so they show on GitHub without running anything.

## Result

On the images I looked at, the boxes sit on the eyes, so the labels look usable for training.

Limits: the notebook reads only the first line of each label file, so if an image has more than one labelled eye, only the first box is drawn and counted. The check is visual, on a handful of images.

## How to run

Easiest: open the notebook on Kaggle and attach the public dataset `icebearogo/eye-detection-dataset`. The paths in the notebook expect it under `/kaggle/input/`.

Locally:

```bash
pip install numpy pandas opencv-python matplotlib jupyter
jupyter notebook eye_detection_analysis.ipynb
```

Then replace the `/kaggle/input/...` paths with your local dataset folder.

## Next step

Train a small YOLO model on this split and report precision and recall on `val`.

## Tech

Python · OpenCV · NumPy · Matplotlib · Jupyter (Kaggle)
