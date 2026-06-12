---
title: "I made my root partition too small"
date: 2009-10-31
forum: General Help
---

### Post by donsy on 2009-10-31
I did a clean install of 9.10 on my Dell Inspiron 1200. The computer is old has only a 30GB hard drive. It previously had 9.04 installed side-by-side with WindowsXP, allowing 15GB for ntfs, and the rest for an extended partition for Ubuntu. The extended partition was about 14GB and contained the logical drives for 9.04. When I installed 9.10 I chose the manual partioning option and deleted the root and swap partitions and created a root partition of 4GB and a /home partition using the rest of the free space, no swap. Both partitions are ext4. Output from fdisk -l follows:```
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1822    14635183+   7  HPFS/NTFS
/dev/sda2            1823        3648    14667345    5  Extended
/dev/sda5            1823        2345     4200966   83  Linux
/dev/sda6            2346        3648    10466316   83  Linux

```The problem is that my root partition, sda5, is already 60% full on a bare system. No other major packages have been installed yet. In hindsight I should have made my root partition 5 or even 6GB. My question is, if additional space is needed would I be able to shrink my /home partition from the left to make room for expanding the root partion from the right? I'm asking because I never resized a partition from the left before and I'm not sure how ext4 would handle this. Yes, I'll backup my data first.

---

### Post by phillw on 2009-10-31
> **donsy said:**
> I did a clean install of 9.10 on my Dell Inspiron 1200. The computer is old has only a 30GB hard drive. It previously had 9.04 installed side-by-side with WindowsXP, allowing 15GB for ntfs, and the rest for an extended partition for Ubuntu. The extended partition was about 14GB and contained the logical drives for 9.04. When I installed 9.10 I chose the manual partioning option and deleted the root and swap partitions and created a root partition of 4GB and a /home partition using the rest of the free space, no swap. Both partitions are ext4. Output from fdisk -l follows:```
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1822    14635183+   7  HPFS/NTFS
/dev/sda2            1823        3648    14667345    5  Extended
/dev/sda5            1823        2345     4200966   83  Linux
/dev/sda6            2346        3648    10466316   83  Linux

```The problem is that my root partition, sda5, is already 60% full on a bare system. No other major packages have been installed yet. In hindsight I should have made my root partition 5 or even 6GB. My question is, if additional space is needed would I be able to shrink my /home partition from the left to make room for expanding the root partion from the right? I'm asking because I never resized a partition from the left before and I'm not sure how ext4 would handle this. Yes, I'll backup my data first.


Nice to see the words 'backup my data' :D

Yeah, gParted can handle that for you. It takes it a while, so relax and let it get on with it.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

has a gr8 over-view of said wee beastie

Phill.

---

### Post by Bucky Ball on 2009-10-31
If you shrink /home you are going to want to expand / but while /home you can do on a running system / you can not. Reason? The partition must be UNMOUNTED to resize. Therefore, to expand the / partition you are going to need to boot from a Live CD. There is also an ISO of Gparted you can download and boot from that.

You can't unmount the partition that is currently running the OS is the bottom line.

---

