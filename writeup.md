# **Finding Lane Lines on the Road** 

### The project goal is to find lane lines on the road using canny edge detection with houge_line

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road

####Road With lanes
[solidWhiteCurve.jpg](./test_images/solidWhiteCurve.jpg): # (Image References)

####Processed output
[test_images_output/solidWhiteCurve_processed.jpg](./test_images_output/solidWhiteCurve_processed.jpg): 

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

To achive the goal on given image, there are many proccess to be follow.

**Grayscale**
    - On this process the given image will be converted to gray image. This help in further to detect the edge.

**gaussian smoothing**
    - On this process we reduce image noise and unwanted details. To achive maximum result kernel is set to 5x5.

**canny edge detection**
    - by now image is ready for detecting edges. 
    - set low_threshold as 50 and high_threshold as 125.
    - After applying max and min threshold remaining edge pixel provide a more accurate representation of real edges in an image.

**region of interest**
    - we dont need all region of the image. So we keep only required region to process further.
    
**houge line**
    - here we convert image space to houge space. so that we could detect stright line in image.

**draw line**
    - In here we calculate line with slope.
    - seperate line and calcualte average
    - calculate draw points with help of y = mx+b
     
        y1 = height of the image
        y2 = y1 * (3/5) position of image
    
        y = mx + b,
        x = (y - b)/m
    
        where,
        b = intercept
        m = slope
    
        x1 = (y1 - intercept)/slope
        x2 = (y2 - intercept)/slope  
        
        to draw line we have x1, y1, x2, y2

**weighted image**
    - an image is masked with drawn image.
    
using above process I have achived desired output. 


### 2. Identify potential shortcomings with your current pipeline


- if there is a slight curves in video, the calculation should be wrong as we have programed for stright line

- As pipeline has tested only on daylight video, it could fail if lane are not visible enough.


### 3. Suggest possible improvements to your pipeline

- As of now it detect only stright line, further improvement can be made to over come curves
