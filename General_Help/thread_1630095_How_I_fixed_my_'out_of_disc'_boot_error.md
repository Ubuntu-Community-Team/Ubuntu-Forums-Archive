---
title: "How I fixed my 'out of disc' boot error"
date: 2010-11-24
forum: General Help
---

### Post by rsnow on 2010-11-24
Although my son has given me a cap with "GEEK" written on it, I think he was referring to my personality rather than my computer skills.

When I encountered the 'out of disk' boot error, I was able to fix it after a couple of weeks of research and trial & error. Here is what worked for me:

1) I downloaded Super Fdisk Bootable CD and burned it to a CD. [www.ptdd.com/manual2.htm](www.ptdd.com/manual2.htm)

2) I used the Super Fdisk option #3 to erase my MBR

3) I used Partition Master (Free) which was also at the same site to create my primary NTFS partition. Note:[I]Before starting all of this, I had already used Gparted to remove all partitions from the drive.[I]

4) Next, I simply installed Ubuntu 10.10 following the prompts to designate the primary partition as root and to create a swap file at the end of the unused portion of the drive.

I hope this helps someone. [/I][/I]

---

### Post by dcstar on 2010-11-25
> **rsnow said:**
> Although my son has given me a cap with "GEEK" written on it, I think he was referring to my personality rather than my computer skills.

When I encountered the 'out of disk' boot error, I was able to fix it after a couple of weeks of research and trial & error. Here is what worked for me:

1) I downloaded Super Fdisk Bootable CD and burned it to a CD. [www.ptdd.com/manual2.htm](www.ptdd.com/manual2.htm)

2) I used the Super Fdisk option #3 to erase my MBR
........

Gparted has the ability to "erase" the MBR: Device-Create Partition Table. There is no need to use additional tools to achieve the same result.

---

### Post by rsnow on 2010-11-26
Thanks for the info. I guess I just couldn't or didn't find that info during my research.

---

