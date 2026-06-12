---
title: "[Lucid] Two Flash problems:  Problems Clicking &amp; Slow Full-Screen Video"
date: 2010-09-06
forum: General Help
---

### Post by eode on 2010-09-06
I had a difficult time finding these, so I figured I'd post them for  others.  They are two separate bugs, but #1 can prevent you from fixing  #2.

This post is to fix two separate flash issues:
#1:  Problems clicking on buttons/closing ads/etc.
#2:  Slow, blocky, choppy full-screen playback.

Note: **You may not have both of these!**   These are separate issues, with separate solutions.  I am just  including them in one post for convenience, as I had both problems on my  system.  **If you do have both problems** on your system, **you will need to fix #1 first!**

**Problem #1:  Problems clicking on buttons/closing ads/etc**
This fixes the problems with clicking on buttons in flash, closing ads,  etc.  It can interfere with changing flash settings, which you need to  do in order to fix the choppy/blocky full-screen playback issue.
[B]Solution:
Step 1) [/B]You need to edit a file as root.  Open up a terminal, and type or paste the following line:[FONT=Courier New]
[/FONT]```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```**Step 2) **You are adding the line "[FONT=Courier New]export GDK_NATIVE_WINDOWS=1[/FONT]" as the next-to-last line in the file.  
The file will probably end up looking like this:
```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer

```**Step 3)**  Save, and close gedit.  You will need to restart Firefox.




**Problem #2:  Slow/choppy/blocky full-screen flash playback**
If you're getting slow/choppy/blocky full-screen flash video, this may help you! 
More detailed instructions [here]("http://www.spotht.com/2010/06/fix-fullscreen-bug-for-flash-videos-in.html").
**Solution:**
**Step 1)**  Right-click on a flash item, like a youtube video or advertisement, and select [B]Settings
Step 2)[/B] Un-Check **Enable Hardware Acceleration**, but don't close the **Adobe Flashplayer Settings**
**Step 3)** In a terminal, execute the following commands:[FONT=Courier New]
[/FONT]```
sudo su
sudo mkdir /etc/adobe
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg

```Step 4) Recheck **Enable Hardware Acceleration**, and click **Close**.
Step 5) Restart your browser.


Hope this is useful!!

---

### Post by lovinglinux on 2010-09-07
See [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html).

---

