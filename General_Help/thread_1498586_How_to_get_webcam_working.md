---
title: "How to get webcam working?"
date: 2010-06-01
forum: General Help
---

### Post by Lucky75 on 2010-06-01
Hi,

I have a crappy usb UVC webcam (iCan brand), but I don't really know how to get it working? Do I need to install any drivers? What software would I use to get it to work? Do I need to enable anything? 

It doesn't seem to be showing video if I open skype, although it does detect that I have something on /dev/video0, and lsusb gives:

Bus 001 Device 007: ID 0ac8:332d Z-Star Microelectronics Corp. Vega USB 2.0 Camera

Any suggestions?

Thanks!

---

### Post by shazbut on 2010-06-01
Have you tested the cam in cheese (available in the repos)?  If it works there but not in skype, you may need to launch skype with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
(32bit system)
or
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```
(64bit system)

as per [this]("https://help.ubuntu.com/community/Webcam") page.

---

### Post by Lucky75 on 2010-06-01
Yeah, cheese can display the video feed fine.

I tried launching skype as you suggested, but when I click on the test in options it doesn't work.

I've also tried viewing it on zoneminder, but the feed was just empty. I could just not know how to set that up properly though.

---

### Post by shazbut on 2010-06-01
I'm fresh out of ideas then, that's what I had to do to get mine working with skype.
Does the 'test' button in skype actually test the cam though?  I thought it was just an audio test.

---

### Post by tgalati4 on 2010-06-01
If it is an older camera then it may only be supported by v4l.  Skype will only detect newer, v4l2 cameras.

If your camera works in xawtv and motion, then find a use for it with motion.  Get a newer camera that is compatible with skype.  You can search the forums (and skype forums) for cameras that work well with skype.

To find out what switches are available for your camera driver:

modinfo -p yourcameradriver

To get your camera driver, look in:

lsmod

It would be the driver associated with USB.

tgalati4@washme:~$ lsmod | grep usb
usbcore               146284  3 gspca,uhci_hcd

In this example, gspca is the camera module.

Sometimes allowing write permission will help with camera detection:

sudo chmod 777 /dev/video0

---

### Post by Lucky75 on 2010-06-01
All I see is this:

snd_usb_audio          84224  1 
snd_usb_lib            16284  1 snd_usb_audio
snd_hwdep               7200  2 snd_usb_audio,snd_hda_codec
snd_pcm                75296  5 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_rawmidi            22176  2 snd_usb_lib,snd_seq_midi
snd                    59204  18 snd_usb_audio,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 38208  1 hid_logitech


What driver would it be?

And it does seem like its using the v4l2 driver, from the errors I get:

```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error setting pixformat: Device or resource busy

```

Chmodding /dev/video0 allowed me to see video from zoneminder, although skype still doesn't work.


Edit:

Actually, now I can't get cheese to work either, although my ZM is still showing the feed fine. Perhaps one is using it so the others can't access it or something?  Although shutting down apache didn't do anything.

Cheese gives:
```
libv4l2: error requesting 4 buffers: Device or resource busy
```

---

### Post by derklempner on 2010-06-01
> **Lucky75 said:**
> Yeah, cheese can display the video feed fine.

I tried launching skype as you suggested, but when I click on the test in options it doesn't work.

I've also tried viewing it on zoneminder, but the feed was just empty. I could just not know how to set that up properly though.
Check out my response in this previous thread: [[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1483825[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1483825")

---

### Post by Lucky75 on 2010-06-01
Unfortunately my webcam isn't working with cheese now either, although it was when I first tried.  

I was already launching it with the LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype, and I manually exported the other setting but it didn't seem to work any better.

I think it might work with skype if I can get it working with cheese now, but I get that "Device or resource busy" error message.

---

### Post by no2498 on 2010-06-02
v4l1 and v4l2 are the same thing now days they put them together

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

retry the cam in cheese

cheese has a very good help file

if it stops again dont open cheese just redo what i said

cheese has all the webcam settings now days also

wxcam works good for me

read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

comes in a deb file also

hope this helps

---

### Post by Lucky75 on 2010-06-03
Yeah, like I was saying before, it seems to be a problem of something using it? I'm not sure. It doesn't work when I test it in gstreamer-properties either. I get the same error messages.

> 
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 640x480 [gstv4l2object.c(1854): gst_v4l2_object_set_format (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src3:
Call to S_FMT failed for YU12 @ 640x480: Device or resource busy]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc2:
Error setting the channel/norm settings: Invalid argument]



---

### Post by Lucky75 on 2010-06-04
up

---

