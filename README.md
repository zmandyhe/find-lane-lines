# **Finding Lane Lines on the Road** 

### Overview
When we drive, we use our eyes to decide where to go. The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle. Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project I will detect lane lines in images using Python and OpenCV.

![original image](https://github.com/zmandyhe/find-lane-lines/blob/master/test_images/solidWhiteRight.jpg)

![annoted image](https://github.com/zmandyhe/find-lane-lines/blob/master/test_images_output/solidWhiteRight.jpg.png)


### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 7 steps. 
1. Read in and grayscale the image
2.  Apply Gaussian smoothing to reduce image noise and details.
3.  Apply Canny edge detection, adjusted double threshold to determine potential edges
4. Create a masked edges image using fillPoly method, adjusted a four sided polygon to mask
5. Run Hough Lines on edge detected image
6. Iterate over the output "lines" and draw lines on a blank image 
7.  Draw the lines on the edge image

In order to draw a single line on the left and right lanes, the key task is to write the draw_lines() function.  I followed the following steps to define the draw_lines function:
1. Read in the orignial image and the Hough lines 
2. Turn Hough lines into array of intercepts(y1-intercept*x1) and slopes (y2-y1)/x2-x1
3. Find the biggest and the smallest slope then average them
5. Find the corresponding (x1,y1),(x2,y2) from the averaged slopes and intercepts
6. Draw lines over the original image.


### 2. Identify potential shortcomings with your current pipeline

It works fine with straight lane lines but when the lane has a relatively larger curves, the accuracy of detecting the lane lines is becoming more challenging. The draw_line function needs to be furtherly improved in the next iteration by developing improved algorithm utilizing more advanced computer vision techniques.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to utilize more advance line detection algorithm to draw the lines.
