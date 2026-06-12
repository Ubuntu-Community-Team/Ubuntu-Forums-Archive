---
title: "Recording from webcam with Cheese(audio problem)"
date: 2009-09-09
forum: General Help
---

### Post by James- on 2009-09-09
When I plug in the Logitech QuickCam Pro 9000 the fallowing appears in my /dev/ folder:

/dev/dsp1
/dev/audio1
/dev/video0

When I go into cheese, I can record the video, but there is no sound and no option to set the sound source. Is there another way to record video/audio from the webcam? I don't mind using console(I would prefer GUI).

Help is appreciated

I've tried capturing with mencoder(with no avail):

```

mencoder tv:// -tv driver=v4l2:width=960:height=720:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder 2:1.0~rc2-0ubuntu19+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM) i7 CPU         940  @ 2.93GHz (Family: 6, Model: 26, Stepping: 4)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (046d:0990)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Floating point exception
```

---

### Post by James- on 2009-09-11
I found out a solution:

It appears that its the auto exposure that is causing the problem, with guvcview you can disable it and record video+audio =)

---

### Post by tommah04 on 2009-09-17
hey, I have this same problem and I was wondering what guvcview is and how exactly to fix auto exposure.... sorry I just got the program and just trying to figure it out

also.... when initially recording a video.... is it temporarily saved somewhere.... I just don't want videos to double count on my hard drive.....thanks!

---

### Post by macabrem on 2009-10-04
> **James- said:**
> I found out a solution:

It appears that its the auto exposure that is causing the problem, with guvcview you can disable it and record video+audio =)


I posted a private message, but I'm hoping you could maybe answer my question here - can you explain what I need to do with guvcview to get my audio to work in Cheese?

---

### Post by James- on 2009-12-10
I never got it to work with cheese, I recorded from guvcview

---

### Post by AkiraBergman on 2009-12-18
Thanks so much James. gucview should be listed as a webcam in Synaptic. It works like a charm.

---

