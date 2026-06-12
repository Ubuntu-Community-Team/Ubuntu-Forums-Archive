---
title: "cheese video recording crashes"
date: 2011-03-02
forum: General Help
---

### Post by sites on 2011-03-02
I just picked up a Microsoft LifeCam Cinema usb webcam.  I installed cheese & it takes pictures just fine & records video as long as the mic isn't enabled.  However, if go to System-Preferences-Sound and change my input to the mic on the webcam cheese will not record video.  When I start recording the window goes black & i have to force quit cheese.  I tested the mic with Sound Recorder & it works. There's nothing in the cheese preferences to change & i don't know where else to start looking. :confused:

EDIT:  I ran gstreamer-properties & the sound test worked.  Still no solution.

---

### Post by sites on 2011-03-02
bumping just to show up under "New Posts"

EDIT: ok that didn't work.. guess my thread will just have to be off the radar for the time being

---

### Post by sites on 2011-03-03
[http://ubuntuforums.org/showthread.php?t=1693472](http://ubuntuforums.org/showthread.php?t=1693472)

---

### Post by rcayea on 2011-03-03
My guess is drivers. Knowing that, here are a couple of websites that might be able to help:

[http://tips-linux.net/en/linux-ubuntu/linux-driver/webcam-linux-drivers](http://tips-linux.net/en/linux-ubuntu/linux-driver/webcam-linux-drivers)


[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)


Also, try using guvcview. It should be in synaptic.

---

### Post by sites on 2011-03-03
Thanks rcayea. Installed guvcviewer & my audio input device was listed as /dev/dsp but when i changed it to /dev/dsp1 i finally got audio in my video recording.  However, i can't find any way to select the audio device in cheese.  Any ideas?

EDIT:  tried changing gstreamer-properties audio device but cheese just locks up whenever i record video so i'll just stick with guvcviewer for video.

---

