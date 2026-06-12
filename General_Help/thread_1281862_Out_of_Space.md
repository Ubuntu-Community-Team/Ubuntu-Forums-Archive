---
title: "Out of Space"
date: 2009-10-03
forum: General Help
---

### Post by topdog2009 on 2009-10-03
Just downloaded Ubuntu and installed on my laptop as a dual boot woth Windows Vista.
Appears to be working OK except that when I try to run a program for the first time i.e. Gimp I get the following error message
 Creating folder '/home/caro/.gimp-2.6'...
Cannot create folder '/home/caro/.gimp-2.6': No space left on device 

When I installed Ubuntu I accepted the default installation suggestions. I do have plenty of space on my hard drive, I assume that I need to increase the partition but do not know how to do this with Ubuntu.

Brian

---

### Post by stephana on 2009-10-03
Hi,

you can try to install gparted:

type this in terminal: sudo apt-get install gparted

with the installed gparted tool you can increase your disk space. After installing you can find it in System->Preferences

---

### Post by snowpine on 2009-10-03
Hi Brian, unfortunately there is a bug in the installer... the default setting is much too small! :(


What you need to do is reboot using the Live CD. Once you are running from the live CD, you can use the Gparted partition editor to resize your partitions. I recommend 10gb minimum for Ubuntu. (You can't resize a partition while you're using it; you need the Live CD... just like you can't change a flat tire while you're driving.)

---

### Post by topdog2009 on 2009-10-03
Wow - Now that is what I call excellent support from the Ubuntu community - thanks guys

Brian

---

