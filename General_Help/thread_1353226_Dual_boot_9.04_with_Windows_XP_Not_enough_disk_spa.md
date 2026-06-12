---
title: "Dual boot 9.04 with Windows XP Not enough disk space for updates"
date: 2009-12-12
forum: General Help
---

### Post by trojanliux on 2009-12-12
Hello,  

I am a linux newb, I installed win xp first with half my partition, then 9.04 with the other half.  But when I try to do the updates in unbuntu it says I don't have enough disk space.

Help Appreciated

---

### Post by FearfulJesuit on 2009-12-12
I understand you split half your hard drive but how much space did you leave on your linux partition? How big is your hard drive? It maybe that your partitions are too small or you installed linux accidentally on an additional smaller hard drive with the xp backup on it. Either way, more details are needed.

---

### Post by mikewhatever on 2009-12-12
Can you post the output of **df -h** from Applications->Accessories->Terminal. The output should show your Ubuntu partition size and how full it is.

---

### Post by trojanliux on 2009-12-12
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 624M     0  624M   0% /lib/init/rw
varrun                624M   92K  624M   1% /var/run
varlock               624M     0  624M   0% /var/lock
udev                  624M  156K  624M   1% /dev
tmpfs                 624M   76K  624M   1% /dev/shm
lrm                   624M  2.4M  622M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/mmcblk0p1        120M   82M   39M  69% /media/disk

---

### Post by mikewhatever on 2009-12-12
As you can see, sda5 is your Ubuntu partition, it's only 2.3GB in size and is 100% full. I think it would be best to start over and partition properly.

---

