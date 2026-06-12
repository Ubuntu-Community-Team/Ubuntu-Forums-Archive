---
title: "webcam in skype with ubuntu 9.10"
date: 2010-02-16
forum: General Help
---

### Post by eppo on 2010-02-16
i'm trying to use my logitech webcam with skype. for some reason it doesnt work. when i go to the settings it see's the webcam but the test doesnt work.
if i load up cheese i can see video from the webcam fine. 
i'm running the most up to date version of skype.
any ideas on how to get it running?

---

### Post by cjhabs on 2010-02-16
In the Skype options -> video
did you check "Enable Skype video" and "start my video automatically when I am in a call".
Also, is the correct video device selected in "Select Webcam"
I am running the latest Skype, with Karmic and a Logitech webcam and it works for me.

---

### Post by Cuba71 on 2010-02-17
I'm also running Skype on Karmic 9.10 with a C-600 Logitech webcam, without any problems

---

### Post by zeroseven0183 on 2010-02-17
I also had that problem before but thanks to this [thread]("http://ubuntuforums.org/showthread.php?p=8815115"). Here's what I did.
To test if this work, open a Terminal and type
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

If the webcam and the audio worked perfectly, you may want to create a shortcut so that you won't type it everytime you run Skype.

1. create a file and name it Skype or launchskype (or whatever)
2. type the following codes and Save
```

#!/bin/sh
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so 
skype &

```
3. right click the icon and set it as executable by checking the "Allow executing file as program" in the Permissions tab
4. make a link and copy it on your desktop

In my case, I modified the shortcut from the Applications menu.

I hope that makes your webcam work in Skype.

---

### Post by eppo on 2010-02-18
when i type that in i get this:
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
what is causing that error?

---

### Post by prkos on 2010-02-18
> **eppo said:**
> when i type that in i get this:
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
what is causing that error?
I'm getting the same error, same symptoms. 

The camera is working fine through luvcview, and I even got it working inside vmware WinXP VSee application, only Skype won't work. 

I tried with Metacity and Compiz, it's the same. When I go to test the video in Skype options I just a white screen (fills my whole screen), and if I double click it the white screen goes away returns to my normal screen.

Edit - more info: 
When I try the 32-bit lib I don't get the error and Skype starts, but when I try the video test in Options I get a bunch of:

X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes)

---

### Post by pablotdl on 2010-09-10
Check this thread [http://ubuntuforums.org/showthread.php?p=9829126](http://ubuntuforums.org/showthread.php?p=9829126)

---

### Post by jaybok on 2011-04-12
You guys are awesome!  that code worked like a charm.  Now lets figure out the shortcut.  Thanks!!!

> **zeroseven0183 said:**
> I also had that problem before but thanks to this [thread]("http://ubuntuforums.org/showthread.php?p=8815115"). Here's what I did.
To test if this work, open a Terminal and type
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```If the webcam and the audio worked perfectly, you may want to create a shortcut so that you won't type it everytime you run Skype.

1. create a file and name it Skype or launchskype (or whatever)
2. type the following codes and Save
```

#!/bin/sh
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so 
skype &

```3. right click the icon and set it as executable by checking the "Allow executing file as program" in the Permissions tab
4. make a link and copy it on your desktop

In my case, I modified the shortcut from the Applications menu.

I hope that makes your webcam work in Skype.

---

