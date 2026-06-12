---
title: "Boot problems ..."
date: 2011-12-13
forum: General Help
---

### Post by w1d3 on 2011-12-13
i got 2 problems at startup i googled for hours with no success the first one is that my system stalls at checking battery state i found out that by selecting ubuntu recovery from the grub menu and if i have luck and it doesn't stall i login and when i type startx it starts to load for a few seconds and stops all i see is a black screen with my mouse pointer when i press ctr alt F1 this is what i see: [http://s10.postimage.org/hx8005cih/IMG_3519.jpg](http://s10.postimage.org/hx8005cih/IMG_3519.jpg)

---

### Post by Bucky Ball on 2011-12-13
What release?

---

### Post by w1d3 on 2011-12-13
> **bucky ball said:**
> what release?
10.04

---

### Post by Bucky Ball on 2011-12-13
That sounds like it might be a graphics driver issue. When you get to the grub menu at boot to select an OS, choose the kernel you want and hit 'e' rather than enter. 

At the end of the line that reads, 'quiet splash' add 'nomodset' then follow the instructions at the bottom of the screen to save changes and boot. See if that makes any diff.

---

### Post by w1d3 on 2011-12-13
it still stops at checking battery state ....

---

### Post by Bucky Ball on 2011-12-13
Is the machine plugged in or running on the battery? Might sound silly, but ...

---

### Post by w1d3 on 2011-12-13
i tried removing the battery and running it only plugged in also without connecting it to the power with the battery and still no difference

---

### Post by gordintoronto on 2011-12-13
What is the brand and model of your laptop?

Can you boot from a LiveCD?

---

### Post by w1d3 on 2011-12-14
its lenovo y550 and yes i can boot from a live cd

---

### Post by gordintoronto on 2011-12-14
That's a large family of computers. Perhaps you could describe what you have: CPU, memory, video adapter, etc.

Did you install a graphics driver after installing Ubuntu?

My first reaction when I see you installed a very old version of Ubuntu is, please try the latest version.

---

### Post by w1d3 on 2011-12-15
> **gordintoronto said:**
> That's a large family of computers. Perhaps you could describe what you have: CPU, memory, video adapter, etc.

Did you install a graphics driver after installing Ubuntu?

My first reaction when I see you installed a very old version of Ubuntu is, please try the latest version.

its old but stable .. 
gpu - nVidia GeForce GT 240M with the latest nvidia drivers
cpu - Intel(R) Core(TM)2 Duo CPU T6600  @ 2.20GHz
ram - SODIMM Synchronous 800 MHz 2x2GB

---

### Post by gordintoronto on 2011-12-15
Are you running Ubuntu Server?

I have seen several anecdotes where the 173 video driver solved problems related to the latest driver. That information probably won't help you much if you can't boot the system -- unless you decide on a re-install.

"Stable" means you don't automatically get major new versions of applications, and you can stick with the same stuff for three years. It does not imply that you have a wonderful version of the kernel.

---

### Post by w1d3 on 2011-12-16
the thing is that i encrypted my home folder i managed to unlock it from a live cd but i couldn't transfer my stuff due to no free space is there any way to get it permanently decrypted and usable with other linux installations

---

### Post by zeplin on 2011-12-17
[SIZE=3]I installed xscreensaver, Ubuntu 11.10  and added xscreensaver to startup applications.  The check battery state boot fail occurred sometimes after doing that.  Removed xscreensaver form startup applications and  problem went away.   Maybe other ways of having this happen but above is at least one of them.[/SIZE]

---

