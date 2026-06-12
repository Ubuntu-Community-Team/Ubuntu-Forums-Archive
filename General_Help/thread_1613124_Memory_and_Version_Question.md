---
title: "Memory and Version Question"
date: 2010-11-04
forum: General Help
---

### Post by digitalpure on 2010-11-04
Ok, so I have been using a Mac for the last 4 years, and love it.   I decided to build a new gaming machine and so I put together a nice little windows machine (and never game on it).   Decided I needed to get back to linux and Ubuntu and so I went all in.   I formatted my 2007 MBP and dual boot mac and 10.10 (running super smooth).

Now, the new windows machine is giving me some headaches.  It is a XII Phenom Tri-core 2.80 with 8GB of ram.   It HAD Widnows 7 64bit Ultimate running on it.

I just reinstalled 10.10 and getting some errors installing 64bit version of things like dropbox, flash, teamviewer etc.  It is giving me a architecture error.   I also noticed that things are a little slow or outright horrid when I really bog the system down (firefox with 5-6 tabs, Rhythmbox playing music, chats etc).  This is all normal for me in the windows side and running smooth.   Ubuntu not so much.

Anyway, so I decided to fire up terminal and check some stuff and I am pretty sure I am only getting 1/2 of what I paid for out of the hardware.  Just looking for some advice and confirmation.

Memory: sudo cat /proc/meminfo
MemTotal:        3354564 kB
MemFree:         1765444 kB

That reads under 4GB of ram if I am not mistaken.

CPU: uname -m -r
2.6.35-22-generic i686

file /sbin/init
/sbin/init: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

If I am not mistaken there it is a 32bit environment.  Now, I was VERY careful to download the 64bit version of Ubuntu.   Curious as to how this could have installed or be running 32bit, and what is the easy way to fix it.   I really am missing those 4GB of ram right now for everyday usage.

IF I have to reinstall it is not the end of the world.   Have a new 90GB OCZ SSD drive coming, and that will go nice with the 4 Samsung 1TB 7200rpm drives that I have in there now.   I was planning on a reinstall anyway to take advantage of the SSD drive as the primary drive.

---

### Post by cascade9 on 2010-11-04
> **digitalpure said:**
> MemTotal:        3354564 kB
MemFree:         1765444 kB

That reads under 4GB of ram if I am not mistaken.

CPU: uname -m -r
2.6.35-22-generic i686

If I am not mistaken there it is a 32bit environment.  Now, I was VERY careful to download the 64bit version of Ubuntu.   Curious as to how this could have installed or be running 32bit, and what is the easy way to fix it.   I really am missing those 4GB of ram right now for everyday usage.


Yes, that is under 4GB, and that is 32bit. 

You should be able to see all your RAM if you install the PAE kernel (just searchf or it with synaptic or software centre)

---

### Post by digitalpure on 2010-11-04
Ahh, so sweet...

MemTotal:        8261708 kB
MemFree:         7555688 kB

Thank you very much.  This is why I love the Linux community as a whole.  Mac community somewhat is like this, but Linux is all about the user and making sure the experience is perfect.   

I set my swappiness down to 5 and holy momma is she moving fast.   BIOS overclock to unlcok 4th core so from tri-core 2.8 to Quad 3.08 all with 8GB of ram and STABLE.   Gotta love Linux.

---

### Post by cascade9 on 2010-11-04
Cool, it worked ;)

---

### Post by digitalpure on 2010-11-04
Yes, I followed the directions here: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE) and installed the generic kernerl with PAE and then removed the 100% generic rebooted and all is great.  

Thanks again.

---

