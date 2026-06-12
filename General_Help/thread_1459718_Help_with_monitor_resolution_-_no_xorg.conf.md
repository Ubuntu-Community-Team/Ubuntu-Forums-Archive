---
title: "Help with monitor resolution - no xorg.conf"
date: 2010-04-21
forum: General Help
---

### Post by Trail0fDead on 2010-04-21
Hi guys, 

For some reason I do not have an xorg.conf file and I'm unsure how to get my resolution to the monitor's native 1680 x 1050. I've been searching the internets and been unable to solve this issue. 

My video adapter is: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

Thanks for the help.

---

### Post by Woody1987 on 2010-04-21
Have you tried the display settings menu in system->preferences ?

---

### Post by Trail0fDead on 2010-04-21
Yes. It only gives me 800x600 or 640x480.

---

### Post by Jive Turkey on 2010-04-21
mmm...I hate when that happens.  I think there is a command that will reconfigure xorg for you and create an xorg.conf for you and then you can adjust it later as needed.

Here's a pretty recent article on it:
[https://wiki.ubuntu.com/X/Config]("https://wiki.ubuntu.com/X/Config")

---

### Post by scouser73 on 2010-04-22
> **Trail0fDead said:**
> Hi guys, 

For some reason I do not have an xorg.conf file and I'm unsure how to get my resolution to the monitor's native 1680 x 1050. I've been searching the internets and been unable to solve this issue. 

My video adapter is: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

Thanks for the help.

Paste these commands into Terminal to create a new Xorg.conf.

Step 1 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
**> sudo nvidia-xconfig**

Step 2 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.
**> sudo nvidia-settings**

---

### Post by john newbuntu on 2010-04-22
Have you tried xrandr :
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

### Post by Grenage on 2010-04-22
> **scouser73 said:**
> Paste these commands into Terminal to create a new Xorg.conf.

Step 1 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
****

Step 2 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.
****

Why would you use nvidia-settings for an Intel card?

**Trail0fDead**: Have a look [here]("http://www.grenage.com/xorg.html").

---

