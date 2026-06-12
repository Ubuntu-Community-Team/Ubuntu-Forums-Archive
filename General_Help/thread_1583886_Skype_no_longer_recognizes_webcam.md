---
title: "Skype no longer recognizes webcam"
date: 2010-09-28
forum: General Help
---

### Post by Coco999 on 2010-09-28
It recognized the webcam alright. But after an update perhaps a couple of months ago, it no longer does. Skype is Beta version 2.1.0.81. If I go to Options, Video devices, it shows me only one option for webcam, namely > USB Camera (05a9:a511) (/dev/video0)I click on test but nothing happens. I can communicate and see the other person, but she doesn't see me

---

### Post by ajgreeny on 2010-09-28
Does the webcam work in cheese or wxcam?

---

### Post by gradinaruvasile on 2010-09-28
Open a terminal and launch this (if you have 64-bit OS installed, search for the correct path):

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

And test the camera.

---

### Post by Coco999 on 2010-09-28
> **ajgreeny said:**
> Does the webcam work in cheese or wxcam?

I don't know what are cheese and wxcam.

After writing the above, I tried with a terminal. cheese operates my webcam and shows my face, while wxcam is unknown.

Thank you

---

### Post by Coco999 on 2010-09-28
> **gradinaruvasile said:**
> Open a terminal and launch this (if you have 64-bit OS installed, search for the correct path):

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

And test the camera.

This did the trick and the camera tests OK. I didn't try with an actual communication but expect no trouble there. 

I would not mind knowing what is the difference from launching Skype in the regular way or thus from a terminal.

Thank you very much.

---

### Post by gradinaruvasile on 2010-09-28
> **Coco999 said:**
> This did the trick and the camera tests OK. I didn't try with an actual communication but expect no trouble there. 

I would not mind knowing what is the difference from launching Skype in the regular way or thus from a terminal.

Thank you very much.

It is not just launched from terminal. The stuff before "skype" is the trick here.
The problem here is that some webcams cannot be used correctly by certain applications (mostly the drivers are the culprits). These applications can be helped by preloading certain .so files (like dll s in Windows) to make possible a correct communication between the application and the cameras driver.
Anyway i am not an expert on v4l1 or v4l2, but i too have a webcam that works only this way in skype (and has no problem in most of the others apps).

Ok, now how to make this permanent:

Open a terminal and type:

```
sudo gedit /usr/bin/skype-video
```

give your password, and paste this in it:

```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

save, quit, then type:

```
sudo chmod +x /usr/bin/skype-video
```

Now you have an executable that will launch skype with the workaround.

How to put it in the menu:

Type

```
alacarte
```

in the terminal.

Then click on the "internet" item in the left pane and find skype in the right pane. Right-click on it, click on properties (or select edit if that button exists on the rightmost bar - anyway just edit that entry).

Change the command:

```
skype
```

to 

```
skype-video
```

Close the menueditor app. Thats it. Now if you click on the skype meny entry, the webcam should work in skype.

---

### Post by dirty_harry on 2010-09-28
Just want to post the wiki page where I found the same information as gradinaruvasile already stated:
[https://help.ubuntu.com/community/Webcam#A%20clean%20start%20for%20skype]("http://ubuntuforums.org/member.php?u=589640")

---

### Post by Coco999 on 2010-09-28
> Ok, now how to make this permanent:

Thank you, gradinaruvasile, for your helpful instructions how to solve my problem. I did as you say and now I can launch Skype in the regular way and have it recognize the webcam. In the way I learned a few very useful things, such as alacarte, to change the menu.

I still wonder why, previous to an update, everything worked properly, and now to achieve the same I had to go into that elaborate procedure.

---

### Post by gradinaruvasile on 2010-09-29
Probably there was a kernel update that changed something - the drivers themselves or something related to the v4l interface.

---

### Post by Coco999 on 2010-09-29
> **gradinaruvasile said:**
> Probably there was a kernel update that changed something - the drivers themselves or something related to the v4l interface.

No doubt the subject is quite complex and it is impossible to cover all aspects in an update. Thank you for your help. I'll close the thread as solved.

---

### Post by Matt 6:27 on 2010-10-18
I gave the suggested fix a go and received the following error in terminal:

X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes)

Repeated attempts yielded the same result.  Not sure what to make of this.  Any ideas out there?

Thanks much!

---

### Post by Matt 6:27 on 2010-10-18
File this one under:  I didn't look quite long enough... sorry for the fire drill.

My issue was tied to Cairo-Dock. I shut it off and disabled it in Startup Applications (under System - Preferences), then rebooted,  tested the video in Skype, and all was well.  Interestingly, after starting Skype first, I can run Cairo-Dock and the two seem to play together just fine.   Seems Skype just has to lead when these two programs dance together.

---

