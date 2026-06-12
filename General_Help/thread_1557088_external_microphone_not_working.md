---
title: "external microphone not working"
date: 2010-08-20
forum: General Help
---

### Post by Achilles124 on 2010-08-20
This is the second microphone that I am trying to get to work and so far no good. 

I have tried everything: alsamixer, pulseaudio volume, regular sound preferences, padevchooser, gstreamer but no luck.

I notice something weird though and maybe you guys can help me out with this:

The input of the mic is always max. So without even speaking in the mic, ubuntu indicates that the mic is being used. So, volume is to the max.

I will include some pics.

---

### Post by Achilles124 on 2010-08-20
My system: Linux ecmpeek-desktop 2.6.32-24-generic-pae #41-Ubuntu SMP Thu Aug 19 02:43:57 UTC 2010 i686 GNU/Linux

I have found a possible solution on this page:

[http://ubuntuforums.org/showthread.php?t=1304657]("http://ubuntuforums.org/showthread.php?t=1304657")

My question is: what do i have to install?
1. linux-backports-modules-alsa-2.6.32-24-generic
or 
2. linux-backports-modules-alsa-2.6.32-24-generic-pae

What is the difference between those two files?

---

### Post by hal8000 on 2010-08-20
> **Achilles124 said:**
> My system: Linux ecmpeek-desktop 2.6.32-24-generic-pae #41-Ubuntu SMP Thu Aug 19 02:43:57 UTC 2010 i686 GNU/Linux

I have found a possible solution on this page:

[http://ubuntuforums.org/showthread.php?t=1304657]("http://ubuntuforums.org/showthread.php?t=1304657")

My question is: what do i have to install?
1. linux-backports-modules-alsa-2.6.32-24-generic
or 
2. linux-backports-modules-alsa-2.6.32-24-generic-pae

What is the difference between those two files?

Goede avonds,
The difference is the kernel version. Open a terminal and type:
uname -a

If you see
anc@orac:~$ uname -a
Linux orac 2.6.32-24-generic-pae #41-Ubuntu SMP Thu Aug 19 02:43:57 UTC 2010 i686 GNU/Linux

Similar to the above then install the pae version.
The pae stands for physical address extensions and allows a 32 bit Operating system to use the full 4G of memory by paging memory in blocks.
If you have less than 4G of RAM you will probably install the first version, Hope that helps.

---

