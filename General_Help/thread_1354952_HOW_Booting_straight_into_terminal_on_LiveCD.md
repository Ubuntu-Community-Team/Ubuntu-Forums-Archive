---
title: "HOW? Booting straight into terminal on LiveCD"
date: 2009-12-14
forum: General Help
---

### Post by jward3010 on 2009-12-14
How do I get Ubuntu to forget about loading the gnome desktop and just boot straight into a console using the LiveCD (or LiveUSB). I assume it's something I add to the kernel line at the splash screen.

I understand on a standard hard disk install I can choose "Recovery mode" and that will get me through to a root console, but I'm specifically talking about on a LiveCD where there is no obvious option for a "Recovery" mode.

The reason for it is I regularly have to boot off a LiveCD to restore my GRUB 2 bootloader (Windows 7 frequently zaps it and nothing can boot, it's a well known bug). The operation to restore the bootloader can be done exclusively from the command line and for that reason I don't need to spend the time loading the desktop and on a Karmic LiveCD that can take a while.

---

### Post by switch10 on 2009-12-14
I'm pretty sure the "alternate" live CD's have that option

---

### Post by switch10 on 2009-12-14
heres the link..

[http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/](http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/)

---

### Post by jward3010 on 2009-12-14
First of all thanks for the quick reply switch10 but here's my predicament and why I can't use Alternate CD's.

I'm an IT technician and I test Ubuntu Live on a lot of laptops and PC's that come in, for that reason I would like to continue using the Live version (I boot it off a 4GB USB key) as I can't test compatibility with an Alternate disk. 

Basically I'm looking for the best of both worlds - having Live mode when I want and also cancelling it when I don't need it.

---

### Post by Neek0 on 2010-11-21
Sorry for resurrecting a year old thread, but i've been trying to find out how to do this for a while and just found the answer. 

Add "text OR s", minus the ""s of course, to the end of the boot options line.  That will boot you into a screen similar to the alternate cd's. Scroll to the bottom and select "root."

There you go, root prompt, text only live cd.

Here is the link where i found the answer, Scroll down to where it says "Text Mode":
[https://help.ubuntu.com/community/BootOptions#Changing the CD's Default Boot Options]("https://help.ubuntu.com/community/BootOptions#Changing the CD's Default Boot Options")

---

