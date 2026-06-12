---
title: "Not able to install Ubuntu on an older desktop"
date: 2012-08-15
forum: General Help
---

### Post by u-noob-tu on 2012-08-15
The other day I went to a Goodwill store my uncle works at to look at the used computer section they have there. I ended up buying a desktop for $36. It works great, but for some reason I can't install Ubuntu on it. When trying to boot from a live CD, it just shows an endlessly blinking cursor in the top left. I get the same result from a USB stick. Unusually, I was able to install Windows 7 from a DVD with no issues. I'm not sure what the issue could be. I suspect it may have something to do with hardware. Since I've only had for about 4 days, I don't know all the specs. Here's what I do know:

Intel Pentium D 2GHz
4GB DDR2 RAM
EVGA GeForce GTX 550 Ti (Added myself. No way I got this for $36) 
I think it has an Intel Motherboard, as that's what it says on the BIOS screen.
Otherwise, I think it was a custom tower.

I'm not sure of the chipset model or type. Aside from the Ubuntu issue, I am quite satisfied with my desktop. Any help is appreciated.

---

### Post by sienile on 2012-08-15
Can you run the installer from within Windows? I would try that and set it up as a dual boot, just in case the install doesn't work.

---

### Post by u-noob-tu on 2012-08-15
> **sienile said:**
> Can you run the installer from within Windows? I would try that and set it up as a dual boot, just in case the install doesn't work.
I haven't ever used Wubi before. That is what you are referring to, right? My only concern is I have a particular way I set up my drives when installing. I have an SSD and 160GB HDD. The SSD is the easy part, I'm just going to split it in half. The hard drive may be trickier. I want to split it in half, one half for Windows to use and the other for Ubuntu. I want the Ubuntu half to be mounted at /home, however, so I can keep as much stuff off the SSD as possible. My other concern is will Wubi be able to resize a partition or drive that is currently in use (e.g. the SSD where Windows is installed)?

---

### Post by sienile on 2012-08-15
I don't know. I installed by booting the CD and never through the Windows installer. I'm sure that there would be an obvious "point of no return" in the install process where you would have a clear idea of whether or not you can configure it as you want. Ubuntu is very well made, so I would almost put money on you being able to. Won't know until you try. If not, you can always cancel the installer before it gets to the point of changing your system.

---

### Post by Mark Phelps on 2012-08-15
Couple of points you need to consider ...

First, Wubi installs INSIDE an existing NTFS partition by creating a single file (root.disk) which Ubuntu then uses to emulate a Linux filesystem.  So, using Wubi, there is no way to split the apps amd data across different partitions.

Second, Linux is not organized like Windows, it doesn't have the "Program Files" convention.  This means that in nearly all cases, you won't have any choice as to where the software gets written.

My advice would be to install Ubuntu entirely on the hard drive.

---

### Post by steeldriver on 2012-08-15
boot appears to halt at blinking cursor - usually means a graphics card / driver issue

this may help:

[http://askubuntu.com/questions/127305/how-to-install-ubuntu-on-a-computer-with-a-nvidia-geforce-gtx-550-ti](http://askubuntu.com/questions/127305/how-to-install-ubuntu-on-a-computer-with-a-nvidia-geforce-gtx-550-ti)

---

### Post by u-noob-tu on 2012-08-15
> **steeldriver said:**
> boot appears to halt at blinking cursor - usually means a graphics card / driver issue

this may help:

[http://askubuntu.com/questions/127305/how-to-install-ubuntu-on-a-computer-with-a-nvidia-geforce-gtx-550-ti](http://askubuntu.com/questions/127305/how-to-install-ubuntu-on-a-computer-with-a-nvidia-geforce-gtx-550-ti)
That looks like it will help. Will report back with any results.

---

