---
title: "No Camera Found (Cheese Webcam), Always on Top Missing"
date: 2010-05-02
forum: General Help
---

### Post by dosox on 2010-05-02
After upgrading from 9.10 to 10.40.. My Cheese webcam doesn't work anymore. It says:
[B]
No Camera Found[/B]!

And also one important thing is missing.. (I don't know how to say that).. "ALWAYS ON TOP"
How do i get back that :(

---

### Post by no2498 on 2010-05-02
for the cam
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

now try the cam in cheese

now to get cheese on the launch panel 
applications sound&video right click cheese add to panel

hope this helps

---

### Post by adoomer on 2010-05-05
I've got a similar problem on MSI Wind U100 netbook. In 9.10 webcam worked well (after fixing the [bug #435352]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352")), but after upgrading to 10.04 Cheese says "No camera found".

According to your advice I performed a gstreamer test. Every video test finished with an error "Device "/dev/video0" not exist."

Below is the terminal output:
```
martyna@martyny:~$ gstreamer-properties 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Urz&#261;dzenie "/dev/video0" nie istnieje. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Nie mo&#380;na zidentyfikowa&#263; urz&#261;dzenia '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline2/GstV4l2Src:v4l2src1:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Custom': Nie mo&#380;na zidentyfikowa&#263; urz&#261;dzenia '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline3/GstV4l2Src:v4l2src2:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Urz&#261;dzenie "/dev/video0" nie istnieje. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline7/GstV4lSrc:v4lsrc2]
```

---

### Post by no2498 on 2010-05-06
try running this in a terminal

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

also look in the add & remove, program

see if you have the. good, bad, and ugly  installed

---

### Post by raimennendez on 2010-11-04
Hi

I followed this tread to solve my camera issue.

I tried to run:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

but it doesn't work for me.

I also upgraded my old Jaunty to Lucid.

Any suggestion?

Thank you

---

