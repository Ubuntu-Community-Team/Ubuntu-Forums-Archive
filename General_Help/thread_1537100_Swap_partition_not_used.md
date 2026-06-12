---
title: "Swap partition not used ??"
date: 2010-07-23
forum: General Help
---

### Post by j0shm4n on 2010-07-23
Hello i have my 4gb swap partition but i think it's not used at all .. i edited my etc/fstab so my os will load swap when starting .. It look like this :
# swap was on /dev/sda3 during installation
/dev/sda3        none            swap    sw              0       0                      total           used    
also u ran free -m command several times but it's always "Swap:         3905          0       
free
3905"
Did Ubuntu uses swap only when my RAM usage goes high or what ?
Sorry for my bad english .

---

### Post by plucky on 2010-07-23
> Did Ubuntu uses swap only when my RAM usage goes high or what ?

Yes,using swap will slow down the machine as it has to use the disk,just think of it as a safety net if you run out of RAM.Running programs in RAM is much faster.

If you don't Hibernate or Suspend,you could reduce the size of the swap partition if you are running out of disk space. 

Good Luck

---

