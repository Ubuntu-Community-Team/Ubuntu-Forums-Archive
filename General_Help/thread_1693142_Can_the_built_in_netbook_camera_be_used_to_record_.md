---
title: "Can the built in netbook camera be used to record video?"
date: 2011-02-22
forum: General Help
---

### Post by cblnchat on 2011-02-22
I have a netbook with a small crappy built in camera.  And it will only take pics with it.  Ive tried the video recorder via Cheese Webcam Booth, and it wont work at all.  It takes a few minutes for it to unfreeze and then another minute or so to go back to the camera when i click on it!  Is there another webcam application i can use to fix this or am i gonna have to live with it?
Also on a sidenote when im taking pics with Cheese and put a filter on it, it lags or wont work at all.  My lil cousins love the filters lol :D

Thanks very much

---

### Post by no2498 on 2011-02-23
this comes from the cheese help FAQ'S
see if it helps any



The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by coldraven on 2011-02-23
Have a try with guvcview, it's in the Software Center

---

### Post by cblnchat on 2011-03-05
> **coldraven said:**
> Have a try with guvcview, it's in the Software Center

Sorry i took so long to get back.
And i found it, but how do i use it.  There doesnt seem to be any buttons for starting recording, or taking pictures

---

### Post by coldraven on 2011-03-05
> **cblnchat said:**
> Sorry i took so long to get back.
And i found it, but how do i use it.  There doesnt seem to be any buttons for starting recording, or taking pictures
The two buttons on the bottom left - Cap. Image - Cap. Video
The other buttons save or load settings.
Maybe you've been looking at something else!

---

### Post by cblnchat on 2011-03-08
> **coldraven said:**
> The two buttons on the bottom left - Cap. Image - Cap. Video
The other buttons save or load settings.
Maybe you've been looking at something else!

oh i see them!  But my netbooks screen is to small to show them!  Is there another way to record or take pics or is there another program i can use?

Thanks

---

### Post by Jouke74 on 2011-03-09
I have an Asus EEE Netbook 1001 and the only thing that works correctly and fast enough to record without hitches is Guvcview, after trying many other ones. The following should also work on other netbooks.

You need to use a trick to make your screen show a resolution higher than 1024x600, namely 1024x786 which can be done with a program called Jupiter: ([http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html](http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html)) but also with a small script:

Scaling the display to 1024x768

First create a script to switch between normal and compressed mode:
[B][I]
mkdir ~/bin
gedit ~/bin/toggle-zoom[/I][/B]

Copy/paste the following script into the window (delete the space before the '#' sign, I don't know how to make the wiki show # without putting a space in front!):

[B][I] #!/bin/sh

if xrandr | head -n1 | grep -q '1024 x 600'; then
  xrandr --output LVDS1 --scale 1.0x1.28
else
  xrandr --output LVDS1 --scale 1.0x1.0
fi
[/I][/B]
Save and exit, and then make the script executable:

***chmod 755 ~/bin/toggle-zoom***

If you just created the ~/bin directory (if it didn't already exist) log out and back in to add it to your path. Then you can open a terminal or press Alt-F2 and run the command by typing:

toggle-zoom

Or you can assign a short-cut key (windows-z) to it in the keyboard shortcut menu.


This was from the following page: 
[https://help.ubuntu.com/community/EeePC/Using](https://help.ubuntu.com/community/EeePC/Using)

---

### Post by no2498 on 2011-03-09
if your using 32 bit try this program wxcam

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

---

### Post by cblnchat on 2011-03-14
> **cblnchat said:**
> oh i see them!  But my netbooks screen is to small to show them!  Is there another way to record or take pics or is there another program i can use?

Thanks

I found a way to make it work and it works perfectly.

Thanks

---

### Post by t0p on 2011-03-14
> **cblnchat said:**
> I found a way to make it work and it works perfectly.

Thanks

Could you please tell us what you did that worked, so other users (me, for instance) can learn from your labours?

Cheers.

---

### Post by cblnchat on 2011-03-15
> **t0p said:**
> Could you please tell us what you did that worked, so other users (me, for instance) can learn from your labours?

Cheers.

I didnt do anything technical.  I just made the screen that has the buttons you push fullscreen and it shows them. lol

---

