---
title: "ubuntu locks at boot if external hdd is plugged in..."
date: 2006-04-11
forum: General Help
---

### Post by sgleo87 on 2006-04-11
I just got an external hdd that connects to my computer with a USB cable. I have formatted it as fat32 in linux and mounted it. I can read and write to it without any problems. 
But when I boot up my computer and the external hard drive is connected to it then ubuntu will lock at "loading modules"
I added the hdd to fstab and this is the entry:

/dev/sdb1    	/mnt/external	vfat    gid=100,umask=002,noexec,noauto,user 0       2

Anybody have any idea what is causing that and how to solve this problem???

---

### Post by jdong on 2006-04-11
It may be a hardware interaction caused by a buggy motherboard. Try turning off "Legacy USB support" or similar options from your BIOS.

---

