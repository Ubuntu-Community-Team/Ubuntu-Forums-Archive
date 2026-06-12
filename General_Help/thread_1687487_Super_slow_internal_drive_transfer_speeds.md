---
title: "Super slow internal drive transfer speeds"
date: 2011-02-13
forum: General Help
---

### Post by Ansemx324 on 2011-02-13
Alright, so I have two 2TB WD20EARS hard drives.

I am essentially trying to copy files between them (my movie database), and am only reaching speeds of 14MB/s.

When I transfer files to either drive connected to my Windows 7 labtop, I get around 60MB/s. In the tower, they are both connected via SATA cable to the MB (all new parts for this computer, so nothing old). In any case, in Ubuntu 10.10 64bit, I can only ever get 14-16MB/s transfer between drives.

Anyone have any idea why this could be happening? I have also checked for DMA issues (since the processor seems to increase use when transfering), but all I get from hdparm -d /dev/sda (or sdb) is an inappropriate ioctl message. I get the same message when trying to check my DVD drive, so idk whats going on there.

Any ideas?? This is driving me insane! I know that the drives can write quickly bc they are fine when copying from windows!

PS: They are aligned correctly (new advanced format), this I know for sure.

---

