# Face Detection using Haar Cascades with OpenCV and Matplotlib

## Name : SABEESHWARAN. P
## Regno : 212225230234
## Date : 06.09.2026

## Aim

To write a Python program using OpenCV to perform the following image manipulations:  
i) Extract ROI from an image.  
ii) Perform face detection using Haar Cascades in static images.  
iii) Perform eye detection in images.  
iv) Perform face detection with label in real-time video from webcam.

## Software Required

- Anaconda - Python 3.7 or above  
- OpenCV library (`opencv-python`)  
- Matplotlib library (`matplotlib`)  
- Jupyter Notebook or any Python IDE (e.g., VS Code, PyCharm)

## Algorithm

### I) Load and Display Images

- Step 1: Import necessary packages: `numpy`, `cv2`, `matplotlib.pyplot`  
- Step 2: Load grayscale images using `cv2.imread()` with flag `0`  
- Step 3: Display images using `plt.imshow()` with `cmap='gray'`

### II) Load Haar Cascade Classifiers

- Step 1: Load face and eye cascade XML files 
### III) Perform Face Detection in Images

- Step 1: Define a function `detect_face()` that copies the input image  
- Step 2: Use `face_cascade.detectMultiScale()` to detect faces  
- Step 3: Draw white rectangles around detected faces with thickness 10  
- Step 4: Return the processed image with rectangles  

### IV) Perform Eye Detection in Images

- Step 1: Define a function `detect_eyes()` that copies the input image  
- Step 2: Use `eye_cascade.detectMultiScale()` to detect eyes  
- Step 3: Draw white rectangles around detected eyes with thickness 10  
- Step 4: Return the processed image with rectangles  

### V) Display Detection Results on Images

- Step 1: Call `detect_face()` or `detect_eyes()` on loaded images  
- Step 2: Use `plt.imshow()` with `cmap='gray'` to display images with detected regions highlighted  

### VI) Perform Face Detection on Real-Time Webcam Video

- Step 1: Capture video from webcam using `cv2.VideoCapture(0)`  
- Step 2: Loop to continuously read frames from webcam  
- Step 3: Apply `detect_face()` function on each frame  
- Step 4: Display the video frame with rectangles around detected faces  
- Step 5: Exit loop and close windows when ESC key (key code 27) is pressed  
- Step 6: Release video capture and destroy all OpenCV windows  

## PROGRAM :
```

import cv2

# Load Haar cascade
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_frontalface_default.xml')

# Read the image
image = cv2.imread('sabii.jpg')

# Check if image was loaded
if image is None:
    print("Error: Image not found.")
else:
    # Convert to grayscale
    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    # Detect faces
    faces = face_cascade.detectMultiScale(gray, scaleFactor=1.1, minNeighbors=5)

    # Draw rectangles
    for (x, y, w, h) in faces:
        cv2.rectangle(image, (x, y), (x + w, y + h), (255, 0, 0), 2)

    # Get screen resolution
    screen_res = 1920, 1080  # You can change this based on your screen
    scale_width = screen_res[0] / image.shape[1]
    scale_height = screen_res[1] / image.shape[0]
    scale = min(scale_width, scale_height)

    window_width = int(image.shape[1] * scale)
    window_height = int(image.shape[0] * scale)

    # Resize image
    resized_image = cv2.resize(image, (window_width, window_height))

    # Show image
    cv2.imshow('Detected Faces', resized_image)
    cv2.waitKey(0)
    cv2.destroyAllWindows()

```

## OUTPUT:

<img width="507" height="546" alt="image" src="https://github.com/user-attachments/assets/2afbbe3f-4b54-4ab4-890d-899bd71127f1" />
<img width="408" height="512" alt="image" src="https://github.com/user-attachments/assets/bb573c3e-016b-456f-9cdb-a32d3315e014" />


<img width="677" height="312" alt="image" src="https://github.com/user-attachments/assets/ce30f60e-49f4-4137-a497-9db901e5a8bc" />

<img width="656" height="311" alt="image" src="https://github.com/user-attachments/assets/d16aea48-4e55-444a-955a-9309a6a0ed05" />


<img width="667" height="307" alt="image" src="https://github.com/user-attachments/assets/5f80c9e4-fd72-426e-a687-69c4a91234e9" />
<img width="408" height="501" alt="image" src="https://github.com/user-attachments/assets/952be939-3368-49a6-ba2f-7957009f606d" />




## RESULT:
thus the given objective of face detection is done sucessfully.
