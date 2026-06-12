---
title: "Slow full screen video"
date: 2010-08-06
forum: General Help
---

### Post by Will130278 on 2010-08-06
I'm running 10.04

Whenever I run a video on full screen mode, whatever format, the playpack is unbearably slow.

This didn't happen under windows.

Anyone know of a fix?

---

### Post by chopinhauer on 2010-08-06
> **Will130278 said:**
> 
Whenever I run a video on full screen mode, whatever format, the playpack is unbearably slow.


My guess is your X server doesn't have the XVideo extension, hence the whole resizing process runs on your CPU and is extremely slow (just like every Flash video).

What does:
```
xvinfo
```
give you?

---

### Post by Will130278 on 2010-08-07
xvinfo gives me this:-


Adaptor #0: "SIS 300/315/330 series Video Overlay"
    number of ports: 1
    port base: 62
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
    number of attributes: 19
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66046)
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is 10)
      "XV_CONTRAST" (range 0 to 7)
              client settable attribute
              client gettable attribute (current value is 2)
      "XV_SATURATION" (range -7 to 7)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -8 to 7)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_SET_DEFAULTS" (range 0 to 0)
              client settable attribute
      "XV_TVXPOSITION" (range -32 to 32)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_TVYPOSITION" (range -32 to 32)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GAMMA_RED" (range 100 to 10000)
              client settable attribute
              client gettable attribute (current value is 1000)
      "XV_GAMMA_GREEN" (range 100 to 10000)
              client settable attribute
              client gettable attribute (current value is 1000)
      "XV_GAMMA_BLUE" (range 100 to 10000)
              client settable attribute
              client gettable attribute (current value is 1000)
      "XV_DISABLE_GRAPHICS" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_DISABLE_GRAPHICS_LR" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_DISABLE_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_USE_CHROMAKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_INSIDE_CHROMAKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CHROMAMIN" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66046)
      "XV_CHROMAMAX" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66047)
    maximum XvImage size: 1920 x 1088
    Number of image formats: 9
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x35315652 (RV15)
        guid: 52563135-0000-0000-0000-000000000000
        bits per pixel: 16
        number of planes: 1
        type: RGB (packed)
        depth: 15
        red, green, blue masks: 0x7c00, 0x3e0, 0x1f
      id: 0x36315652 (RV16)
        guid: 52563136-0000-0000-0000-000000000000
        bits per pixel: 16
        number of planes: 1
        type: RGB (packed)
        depth: 16
        red, green, blue masks: 0xf800, 0x7e0, 0x1f
      id: 0x55595659 (YVYU)
        guid: 59565955-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x3231564e (NV12)
        guid: 4e563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 2
        type: YUV (planar)
      id: 0x3132564e (NV21)
        guid: 4e563231-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 2
        type: YUV (planar)
  Adaptor #1: "SIS 315/330 series Video Blitter"
    number of ports: 16
    port base: 63
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
    number of attributes: 1
      "XV_SET_DEFAULTS" (range 0 to 0)
              client settable attribute
    maximum XvImage size: 2046 x 2046
    Number of image formats: 7
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x55595659 (YVYU)
        guid: 59565955-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x3231564e (NV12)
        guid: 4e563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 2
        type: YUV (planar)
      id: 0x3132564e (NV21)
        guid: 4e563231-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 2
        type: YUV (planar)

---

### Post by chopinhauer on 2010-08-07
Ok, so you **do** have support for XVideo. The following instructions apply to the GStreamer version of Totem (the default video player), this is the default since Karmic Koala, but if you are using an older version you need to install the package totem-gstreamer ('sudo apt-get install totem-gstreamer').

Run the
```
gstreamer-properties
```
application and under the Video tab choose 'Xv' as your video output.

Does it run faster now?

---

### Post by Will130278 on 2010-08-07
I tried the above.

When I refer to slow video playback I am mainly referring to online flash videos like youtube etc.

the above action has no effect on youtube videos

---

### Post by chopinhauer on 2010-08-07
> **Will130278 said:**
> 
When I refer to slow video playback I am mainly referring to online flash videos like youtube etc.


That is because Adobe Flash is quite bad on Windows, on Linux it's even worse.

In a [recent blog post](http://blogs.adobe.com/penguinswf/2010/01/solving_different_problems.html) the engineers of Adobe explain while Flash is painfully slow (especially on Linux) and in another post they explain why they arbitrarily choose when to use hardware acceleration (basically you need to use proprietary drivers).

The only solution is to ignore Flash and switch to better technologies for video like HTML5. Youtube has an [experimental feature](http://www.youtube.com/html5) in testing and you can join the test by using one of the Firefoxes from [Mozilla PPA](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa).

---

### Post by clhsharky on 2010-08-07
Will130278

Adobe flash gives better support in windows, and less support(no hardware acceleration) in Linux. You can blame Adobe for there lack of support, Linux cant do anything to Adobe flash because its closed source.
With out hardware acceleration a faster cpu clock is needed for equal playback. 
One solution is to down load the flv file and play in a media player.

Check out
Flash Optimization by lovinglinux
[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)
and also
FlashVideoReplacer
[http://flvideoreplacer-extension.blogspot.com/](http://flvideoreplacer-extension.blogspot.com/)

Sharky

---

### Post by lostinberlin on 2010-09-13
Hi,

might not be what you're looking for but here's my 'long sought after  and highly satisfying' solution - depending on your priorities.

Turn off "desktop effects". It's as simple as that. If you can't live  without them, you could find a shortcut to turn them on or off at will,  but I am quite happy without them and the video play back is fantastic.

There you have it. Hope someone finds this useful. Please post elsewhere  and spread the word if it worked for you so that others may get the  benefit. It took a long time to realise the connection.

Stats:
Kubuntu 10.04 (64-bit)
Thinkpad W510 (1920 x 1080)
NVidia Driver: 256.44

---

### Post by Jazzy_Jeff on 2010-09-13
It also does not help that you have a SIS video adapter. The have very poor support under Linux.

---

