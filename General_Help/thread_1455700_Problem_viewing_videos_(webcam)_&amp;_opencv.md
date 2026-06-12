---
title: "Problem viewing videos (webcam) &amp; opencv"
date: 2010-04-16
forum: General Help
---

### Post by Mecasickle on 2010-04-16
Hey guys, I have a problem for viewing my webcam real-time captured videos.

I seem to complie everything correctly and even add these terms to the terminal so I can use my webcam:

export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
camorama

to test camorama (that works perfectly)

but when I try to use an application like this:

./facedetect_net --cascade="/home/manueldeza/Documents/OpenCV/downloads/OpenCV-2.0.0/data/haarcascades/haarcascade_frontalface_alt.xml" /dev/video0

The program starts "running", but I don't see a window view of what the camera is perceiving. Which is really weird, and my best guess is that there is some type of error on configuring the webcam.

Now , it looks like I got this as a error:

libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

Corrupt JPEG data: premature end of data segment
OpenCV ERROR: Null pointer (null filename)
    in function cvLoadImage, loadsave.cpp(380)
Terminating the application...
    called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
    called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
    called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
    called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
    called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
    called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
    called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
    called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
    called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...


Plus when I run camorama , by the terminal I get this warning:

(camorama:3801): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated


Any suggestions?!

Thanks =D

---

### Post by no2498 on 2010-04-16
try your cam in this program wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

getdeb also has it

hope this helps

---

### Post by Mecasickle on 2010-04-17
Haven't tried the program yet, but what I really need is to activate the camera from the terminal to use my openCV programs. I really can't find much coherence in the error since, I googled :

"
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small
"

and most of the similiar errors & respective solutions implied that Cheese Webcam Booth was also malfunctioning. This isn't my case, since cheese and CAmorama do work. What apparently doesn't is that the progrma isn't reading correctly the webcam for my openCV programs. Can gstreamer have anything to do with this? Whould I reinstall libv4l,libv4l2,gstreamer?

Thanks!

---

### Post by Mecasickle on 2010-04-17
Now, I am also getting this error:

HIGHGUI ERROR: V4L2: getting property #5 is not supported
Capture properties (widthxheight - frames): 640x480 - -1
Segmentation fault


when I run another openCV program. Suggestions?

---

### Post by no2498 on 2010-04-17
open a terminal type gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test buton for each 1
 and do not open cheese

---

### Post by 0x656b694d on 2010-09-26
Hi,
I experience the same problem with opencv tests:
```

$ ./capture-cam.py 
OpenCV Python capture video
HIGHGUI ERROR: V4L2: getting property #5 is not supported
Erreur de segmentation (core dumped)

```
v4l2 test in gstreamer-properties works fine (while v4l1 doesn't).

The 'camera' is actually my tv-tuner card.

---

### Post by 0x656b694d on 2010-09-26
wow, i've just took the latest development version of opencv, and got compiz head-tracking plugin working.

---

### Post by bleedingpowers on 2011-07-16
> **Mecasickle said:**
> Now, I am also getting this error:

HIGHGUI ERROR: V4L2: getting property #5 is not supported
Capture properties (widthxheight - frames): 640x480 - -1
Segmentation fault


when I run another openCV program. Suggestions?

Did you ever find out how to set the FPS in a camera in OpenCV with V4L?

I'm having this annoying lack of capability

```
HIGHGUI ERROR: V4L: Property <unknown property string>(5) not supported by device
```

please advise if you can.

---

### Post by no2498 on 2011-07-16
they only use a piece or two of v4l now now its v4l2

put this in a terminal
add the name of the program you use to the back

export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so

you must do this every time till you make it a bin bash file

---

### Post by bleedingpowers on 2011-07-16
It worked the first time I used it, but then I recompiled my code with a small change, and run the export again, but it stopped working...weird!

I did something as you suggested

```
$ cd to_executable_path
$ export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so executable_name

```

---

### Post by no2498 on 2011-07-17
in gstreamer-properties you may need to set the plugin to auto find your cam

---

### Post by bleedingpowers on 2011-07-17
Unfortunately, it does not help by making sure that the plugins that *gstreamer-properties* uses are set to "Autodetect" for Default Output, and "v4l2" for Default Input.

I'm wondering what role is *gstreamer* playing here. Is OpenCV using it? I thought it should be using *v4l* directly.

---

### Post by bleedingpowers on 2011-07-17
I'm going to try capturing the video outside of OpenCV with help of [libv4l2cam]("http://code.google.com/p/libv4l2cam/") and follow the advise from [here]("http://old.nabble.com/Re%3A-OpenCV-Overo-Webcam-p29446414.html")
> Take two files from libv4l2cam. That is libcam.h and libcam.c. Add the header file to the project.

I will be posting my results if they turn out successful.

---

### Post by cenau on 2011-08-04
HI guys, 

>HIGHGUI ERROR: V4L2: getting property #5 is not supported

property #5 is fps - what worked for me was commenting out the bit in the code that gets fps, and just set it manually. eg, changing the lines about fps in capture-cam.py from 
```

     # get the frame rate of the capture device
    fps = highgui.cvGetCaptureProperty (capture, highgui.CV_CAP_PROP_FPS)
    if fps == 0:
        # no fps getted, so set it to 30 by default
        fps = 30
```
to

```
# get the frame rate of the capture device
   # fps = highgui.cvGetCaptureProperty (capture, highgui.CV_CAP_PROP_FPS)
   # if fps == 0:
        # no fps getted, so set it to 30 by default
    fps = 30
```

---

### Post by bleedingpowers on 2011-08-04
I don't think that by saying > fps = 30 you are actually setting the FPS of your capture device. I believe you must try something like this:
```
cvSetCaptureProperty(capture, CV_CAP_PROP_FPS, 30.0)
```

---

