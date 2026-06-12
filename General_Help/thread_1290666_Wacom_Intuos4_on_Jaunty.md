---
title: "Wacom Intuos4 on Jaunty"
date: 2009-10-13
forum: General Help
---

### Post by Kerie on 2009-10-13
Wacom Intuos4 on Jaunty

I am trying to use Wacom Intuos4 on Ubuntu 9.04 on a 64-bit PC, following the instructions on [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

Synaptic shows me that Wacom-tools and xserver-xorg-input-wacom have the installed versions 1:0.8.2.2-Oubuntu2. 

custom_wacom.fdi is installed in /etc/hal/fdi/policy 

In Gimp, in Edit/Preferences/InputDevices/Configure Extended Input Devices, my only choice is Macintosh mouse button emulation (I am not working on a Macintosh), or USB Optical Mouse - but there is no choice for "stylus", as in the instructions. 

The same problem presents in Inkscape.

Can someone suggest what I have missed, or what I should do next?

---

### Post by Favux on 2009-10-13
Hi Kerie,

Welcome to Ubuntu Forums!

The problem is that the Intous4 is new enough that the 0.8.2-2 wacom.ko that comes default with Jaunty doesn't allow usb communication with your tablet.  You need to compile a newer wacom.ko, 0.8.3-2 or up, and replace the default wacom.ko.  Not the rest of the Jaunty linuxwacom packages, just the wacom.ko (the usb kernel driver/module).

This post links you to a HOW TO on how to do this and also talks about replacing the default wacom.fdi.  It also has a link to the Intuos4 thread which shows you how to set up the pad (buttons on the tablet).  Post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Good luck!

---

### Post by Kerie on 2009-11-11
> **Favux said:**
> Hi Kerie,

Welcome to Ubuntu Forums!

The problem is that the Intous4 is new enough that the 0.8.2-2 wacom.ko that comes default with Jaunty doesn't allow usb communication with your tablet.  You need to compile a newer wacom.ko, 0.8.3-2 or up, and replace the default wacom.ko.  Not the rest of the Jaunty linuxwacom packages, just the wacom.ko (the usb kernel driver/module).

This post links you to a HOW TO on how to do this and also talks about replacing the default wacom.fdi.  It also has a link to the Intuos4 thread which shows you how to set up the pad (buttons on the tablet).  Post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Good luck!


Dear Favux

Thank you for your help.  I have followed the instructions from your post #176, and from section 1 of gali98's post #104.

I compiled the module and did 'make', but did not do 'sudo make install' as instucted, and copied it to /lib/modules.

Now we have the situation shown below:

keri@mat:/lib$ ls -l modules/2.6.28-15-generic/kernel/drivers/input/tablet/
total 168
-rw-r--r-- 1 root root 18104 2009-09-09 22:19 acecad.ko
-rw-r--r-- 1 root root 40976 2009-09-09 22:19 aiptek.ko
-rw-r--r-- 1 root root 22680 2009-09-09 22:19 gtco.ko
-rw-r--r-- 1 root root 18320 2009-09-09 22:19 kbtab.ko
-rw-r--r-- 1 root root 53265 2009-11-11 14:48 wacom.ko
keri@mat:/lib$ ls -l modules/2.6.28-11-generic/kernel/drivers/input/tablet/
total 164
-rw-r--r-- 1 root root 18104 2009-04-17 13:35 acecad.ko
-rw-r--r-- 1 root root 40976 2009-04-17 13:35 aiptek.ko
-rw-r--r-- 1 root root 22680 2009-04-17 13:35 gtco.ko
-rw-r--r-- 1 root root 18320 2009-04-17 13:35 kbtab.ko
-rw-r--r-- 1 root root 50688 2009-04-17 13:35 wacom.ko
keri@mat:/lib$ 

and Synaptic shows that 0.8.2.2-0 is the latest and the installed version.

How do I fix this?

Many thanks for your patience!

---

### Post by Favux on 2009-11-11
Hi Kerie,

I don't understand what you are asking.  I see that you compiled a wacom.ko today (you are ahead on the date line?) and installed the modified wacom.fdi.

What needs fixing?

---

### Post by Kerie on 2009-11-12
> **Favux said:**
> Hi Kerie,

I don't understand what you are asking.  I see that you compiled a wacom.ko today (you are ahead on the date line?) and installed the modified wacom.fdi.

What needs fixing?


Hi Favux

Although I had done those instructions mentioned previously, still there was no response in the wacom - it was not being recognised. My mistake here was thinking that at this junction something needed fixing - clearly it did not. 

So then, on further reading, as you had mentioned (in 
[http://www.uluga.ubuntuforums.org/showthread.php?t=1285072&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1285072&page=2))

I did
gksudo gedit /etc/modules 

and then added the word 'wacom' to the bottom of that file. 

Immediate success! So that at last the wacom is recognised and the pen works - at least as far as my quick test goes, I may still have to a lot of refinement to do I'm guessing.

Many thanks Favux - these posts on ubuntuforums are invaluable, as is your clear way of communicating - much appreciated. 

(And yes, I'm ahead in Oz)

---

### Post by Favux on 2009-11-12
Hi Kerie,

Nice job!  You're welcome.  And thank you for the kind words.

---

