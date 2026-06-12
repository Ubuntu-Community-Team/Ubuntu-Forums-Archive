---
title: "Webcam issues"
date: 2010-05-15
forum: General Help
---

### Post by sbelz79 on 2010-05-15
I just got a new webcam.  It's a Creative Live! Socialize HD.  I'm running Ubuntu 10.04 64-bit.  In Skype, when I go to Options>video devices, it shows up under "Select webcam" as "VF0610 Live! Cam Socialize HD (/dev/video0)"  However, when I click Test, nothing happens.  When I double-click on Test, I get a full screen view of a blank window.  Running skype from the terminal, I get the following output:

```
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 

```

Under the advise of an article which can be found here: 

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

I tried running the following command in the terminal:

```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'

```
and then tried the webcam test again, with the same result and output.  I tried again, but with this command:

```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype'
```

with the same results and output. 

However, my webcam works fine with Cheese, so I know I've got the drivers.

Any ideas?

---

### Post by sbelz79 on 2010-05-16
bump

---

### Post by Linuxforall on 2010-05-16
Is your cam recognized by dmesg, install cheese and see if it works.

---

### Post by sbelz79 on 2010-05-16
I already have Cheese, and my cam works fine in it.  I don't know anything about dmesg.

---

### Post by sbelz79 on 2010-05-18
bump.

---

### Post by sbelz79 on 2010-05-29
A new development.  Although testing the camera still gets me the same results, I decided to Skype my girlfriend on her computer on the other room- Both sound and video worked (though the video is pretty choppy).  Is it possible that I need to install a different driver?  If so, how do I find out which one, and how do I install it?

---

### Post by derklempner on 2010-05-29
> **sbelz79 said:**
> I tried running the following command in the terminal:
```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'

```
and then tried the webcam test again, with the same result and output.  I tried again, but with this command:
```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype'
```
with the same results and output.
I had similar issues with Skype, and was able to fix the problem by creating a small bash script to launch Skype and that read thusly:
```
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
Although it was not necessary to include the third line (except the "skype" command to launch the program) to get the camera working properly.

My camera is a Logitech QuickCam Pro 9000, and I found the answer to this issue on the Skype forums [_[COLOR="Red"]here[/COLOR]_]("http://forum.skype.com/topic/411411-problem-with-linuxtv/").

---

### Post by sbelz79 on 2010-05-30
Thanks!  That worked perfectly.

---

