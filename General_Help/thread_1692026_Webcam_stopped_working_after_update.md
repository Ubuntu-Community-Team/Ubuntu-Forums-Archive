---
title: "Webcam stopped working after update"
date: 2011-02-20
forum: General Help
---

### Post by Deeday on 2011-02-20
Something in the last batch of updates proposed by Update Manager (after 13 Feb 2011) broke my webcam, although I cannot pinpoint which one. It was working last week, but now I'm getting this, from **gstreamer-properties**:
```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
libv4l2: error turning on stream: No such device
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'.
[gstv4l2object.c(1983): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: No such device]

```
This is the output from **lsmod | grep video**:
```
videodev               49359  1 gspca_main
v4l1_compat            15519  1 videodev
v4l2_compat_ioctl32    12614  1 videodev
video                  22176  1 i915
output                  2527  1 video

```
I tried with the previous kernel (35-26) and it doesn't work either, so it must be something else. Has anyone had similar troubles?
Thinking about it, last week I also put some more memory into my laptop (from 1 GB to 2.4 GB) but I'd be surprised if it had any relevance.

Thanks for any help :confused:

Maverick 64 bit
Kernel 2.6.35-27
Acer Aspire 5630 with integrated webcam
Intel Core 2 T5500 1.66 GHz

---

### Post by no2498 on 2011-02-21
does the cam light come on at all
? how did you turn it on for the very first fn+f2 keys ?

---

### Post by sit properly on 2011-02-21
Yep, the same thing happened to me. I've got a Dell Inspiron 1440. 

"Cannot connect to video device (/dev/video0)."

Light isn't coming on.  All was working fine till Saturdayish.

---

### Post by Deeday on 2011-02-21
> **no2498 said:**
> how did you turn it on for the very first fn+f2 keys ?

Not sure what you mean mate. The webcam used to switch on automatically (e.g during a Skype call). Pressing Fn+F2 does nothing at the moment.

No, the webcam's light stays off (it used to come on, when the webcam was working).

Anyone has got any idea? :-(

Cheers.

---

### Post by no2498 on 2011-02-22
i have seen in past few mouth's some have had to reinstall gspca
they did it by doing a mod prob some how
mod prob gspca 
put that in google
sorry i cant help any more than that

---

### Post by Deeday on 2011-02-24
[CENTER]**[SIZE="3"]Something _is_ (randomly) working  :confused:[/SIZE]**[/CENTER]

If I open gstreamer-properties -> Video -> Input and change Device from Default to Camera and then back to Default - pressing Test each time - **sometimes** I get the picture from the camera up, but not consistently.
The other times I get either of two slightly different error messages:

```
Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device "/dev/video0". [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: No such file or directory]
libv4l2: error turning on stream: No such device
``` or ```
Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video1'. [gstv4l2object.c(1983): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src2:
system error: No such device]

```

The webcam never works in Skype anyway. I've even disabled the Flash plugin, and npviewer is not running.

Sorry, I have no idea what to do with gspca: it doesn't even come up in Package Manager.

I've reformatted my laptop and done a _fresh Maverick install_, but no joy.

Am I really the only one that has found that something b*ggered up the webcam in the last week or so?? :frown:

---

### Post by no2498 on 2011-02-25
see if installing xawtv helps
and you can try cheese after you install xawtv
xawtv loads a grabber

---

### Post by isa.dsouza on 2012-10-21
It may have something to do with the physical location of the webcam. try pressing the area around the webcam.

---

### Post by wildmanne39 on 2012-10-21
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

