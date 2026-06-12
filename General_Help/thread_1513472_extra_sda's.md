---
title: "extra sda's ???"
date: 2010-06-19
forum: General Help
---

### Post by spiky001 on 2010-06-19
Hi I put this in terminal and found 2 extra sda's, dose any one know how they got there it must of been from install and is there a way to get rid of them sda3 and sda4

spiky@linux:~$ sudo sfdisk -l

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   1911    1912-  15358108+   7  HPFS/NTFS
/dev/sda2       1912    9728    7817   62790052+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       1912+   3735    1824-  14651248+  83  Linux
/dev/sda6       3736+   3917     182-   1461883+  82  Linux swap / Solaris
/dev/sda7       3918+   9728    5811-  46676826   83  Linux
spiky@linux:~$

---

### Post by megamandos on 2010-06-19
Are you using GPT style disk partition table?

if not then:

I noticed that ubuntu does that when setting up partitions sometimes, they are just partitions with 0 space in them, if they really bother you then just use gparted to deleted them, and then run the command "sudo grub-update".

---

### Post by spiky001 on 2010-06-19
ok thk's for that thought I had done something wrong

---

