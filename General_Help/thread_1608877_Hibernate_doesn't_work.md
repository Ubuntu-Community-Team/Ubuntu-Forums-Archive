---
title: "Hibernate doesn't work"
date: 2010-10-29
forum: General Help
---

### Post by Nostigex on 2010-10-29
When I try to hibernate, the computer just goes to a blank, black screen and doesn't turn off. I have to hold the power button to get it to shut down, and when I turn it back on none of the programs running before hibernation have been saved.

---

### Post by Nostigex on 2010-11-06
1 week without reply.
Bump!

---

### Post by Nostigex on 2010-11-11
Bump

---

### Post by dogbite3000 on 2010-11-11
Im not an expert, but i remember reading that it required a certain amount of memory to do. This is HD space.  Also, i read somewhere that if you installed through wubi, and not actually installed using a CD to a new partition, it wouldnt work. 

This is just reading i did a while ago, dont quote me or hold me to it. I'm a beginner to linux myself.

---

### Post by Nostigex on 2010-11-12
I'm pretty sure I have enough memory (2 GB) and hard drive space (23 free GB in home folder).

I installed using a CD to a new partition.

---

### Post by bryangwilliam on 2010-11-12
What hardware are you using? I have heard of many issues with hibernation/sleep one machines with newer hardware. Mine in particular has the issue because the USB 3.0 drivers are not fully supported in those modes and must be unloaded first.

---

### Post by sgage on 2010-11-12
Evidently you need to have an amount of swap space greater than your RAM. However, it might be easier if you just ```
sudo apt-get hibernate
``` and install a script that seems to get everything done right. I could never hibernate my rig until I installed hibernate.

---

### Post by bcbc on 2010-11-12
Look in /var/log/syslog for messages prefixed by **PM:**
They should tell you any errors. (grep 'PM:' /var/log/syslog)


in general, you need a swap partition (not file) that is > size of RAM, and the uuid of the swap needs to be in /etc/initramfs-tools/conf.d/resume

instead of hard shutdowns, try ALT+SysReq R-E-I-S-U-B (it's safer)

---

### Post by AllanP on 2010-11-21
> **Nostigex said:**
> When I try to hibernate, the computer just goes to a blank, black screen and doesn't turn off. I have to hold the power button to get it to shut down, and when I turn it back on none of the programs running before hibernation have been saved.
Did you ever get it to work? I've been trying to get mine to work forever without results and for that reason am primarily in Windows 7 now; never thought I'd say that but, everything just works.
Most of my search results are to do with laptops.
I gave up entirely with my laptop.
On my PC I have 8GB's RAM and a swap of 6GB. I can't see where increasing my swap to more than 8GB's would make any difference.

Regards, Allan

---

