# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 8 steps. 

1. I converted the images to grayscale.

2. I applied Gaussian blurring to the grayscale image.

3. Then I applied trapezoidal region masking to identify the area of interest of the image which consisted the lane lines.

4. I applied the Canny edge detection algorithm to identify the lane edges in the masked region

5. I applied Hough propbabilistic transform to get line segments in the image.

6. I identified segments belonging to the left and right images by identifying the two groups of parallel line segments and dividing them according to their angles. Here, if a line segment in had an angle too different from the rest (identified using the standard deviation of the angles), then it was filtered out to increase the robustness.

7. Each group of line segments was rotated till it was roughly horizontal and the average y-coordinate was found, along with the minimum and maximum x-coordinate to get an averaged out horizontal line. The horizontal line is rotated back to get the average of the lane line. This line was extrapolated so that it always starts at the bottom of the image.

8. The lane lines were drawn on the original image.

### 2. Identify potential shortcomings with your current pipeline

Potential shortcomings:
1. Only works on straight roads
2. Lines do not always end at the horizon


### 3. Suggest possible improvements to your pipeline

Possible improvements:
1. A smoother output could possibly be obtained by average through frames.
2. Color detection can be added as an extra step, for example to improve stabilitz against shadows, cracks etc.
3. Line could be extrapolated towards the horizon too.
