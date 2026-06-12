---
title: "Help installing drivers"
date: 2010-06-11
forum: General Help
---

### Post by sokekoke on 2010-06-11
Hello! I'm totally new on linux ubuntu so a lot of confusing stuff going on.

I'm trying to follow a guide to get my graphic card to work. I have a laptop asus UL80VT with a button to switch between a nvidia geforce G210M and onboard intel.

the guide:


> 
this is how you get g210m to work on ubuntu 9.10 / 10.04.

1. download and install nvidia drivers. (i have only tested the ones in the repos)

2. make sure you got an Xorg.conf that is correct. ( if not, run nvidia-xconfig )

3. reboot into bios (press delete while booting)

4. change the SATA option in the bios from enhanced to compatibility. ( yea, this makes sense? NOT! )

5. boot into linux and smile!

How do i find and install the correct nvidia drivers from this repo? (step1)
:-)

**EDIT: got the gfx drivers to work!**

Also, i can't seem to disable my mousepad, any suggestions?

If you guys can recommend me some basic documentation to read on the workings of ubuntu would be glad !

Thanks!!

---

### Post by Jakiejake on 2010-06-11
> **sokekoke said:**
> Hello! I'm totally new on linux ubuntu so a lot of confusing stuff going on.

I'm trying to follow a guide to get my graphic card to work. I have a laptop asus UL80VT with a button to switch between a nvidia geforce G210M and onboard intel.

the guide:




How do i find and install the correct nvidia drivers from this repo? (step1)
:-)


System -> Adminstration -> Hardware Driver :D

---

### Post by Jakiejake on 2010-06-11
> **sokekoke said:**
> 
Also, i can't seem to disable my mousepad, any suggestions?

If you guys can recommend me some basic documentation to read on the workings of ubuntu would be glad !

Thanks!!

Mouse Pad?
Take it off your desk!
I assume you mean touch pad or track pad like on a laptop
System -> Preferences -> Mouse

---

### Post by sokekoke on 2010-06-11
Wen i go to "System > administrator > hardware drivers" i get a window that says "No proprietary driver are in use on this system"

then i can activate "Nvidia accelerated graphic drivers" but when i boot the pc i get black screen and have to reinstall (tryed this:-) )

 - Is this what step1 is? 

also i cant find any *touch pad *setting under the "mouse" menu

---

### Post by Jakiejake on 2010-06-11
> **sokekoke said:**
> Wen i go to "System > administrator > hardware drivers" i get a window that says "No proprietary driver are in use on this system"

then i can activate "Nvidia accelerated graphic drivers" but when i boot the pc i get black screen and have to reinstall (tryed this:-) )

 - Is this what step1 is? 

also i cant find any mousepad setting under the "mouse" menu

Are you on a laptop?

---

### Post by sokekoke on 2010-06-11
> **Jakiejake said:**
> Are you on a laptop?

Yes sir! Asus UL80VT laptop

---

### Post by sokekoke on 2010-06-11
I found this post: [http://ubuntuforums.org/showthread.php?t=1298198](http://ubuntuforums.org/showthread.php?t=1298198)

i can enable/disable my *touch pad* with these commands:

enable: sudo modprobe -r psmouse
disable: sudo modprobe psmouse

---

### Post by Jakiejake on 2010-06-11
> **sokekoke said:**
> I found this post: [http://ubuntuforums.org/showthread.php?t=1298198](http://ubuntuforums.org/showthread.php?t=1298198)

i can enable/disable my mousepad with these commands:

enable: sudo modprobe -r psmouse
disable: sudo modprobe psmouse

Awesome! :guitar:

---

### Post by sokekoke on 2010-06-11
SO i tryed to install synaptics touchpad:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

when i run the program it says:

> GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics


but when i do this:

gksudo gedit /etc/X11/xorg.conf

the file is empty/blank :confused:

**EDIT: i realize that my touch pad is a "ELAN smart pad" duh, thought was synaptics**

---

