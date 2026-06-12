---
title: "Windows does not see two partition NTFS any more (Ubuntu does)"
date: 2009-12-05
forum: General Help
---

### Post by Ryantoss on 2009-12-05
My English is not so good so i will make it short

Well this is my situation

1. I got three partition (NTFS) and first one C: is for windows (NTFS)

2. Created one more partition for Ubuntu

3. Using dual boot so i have two OS now

4. I was mess up with new format of OS (also swapping as well), it format my NTFS.

5. I format these two partition from Ubuntu (NTFS), though that both windows and linux can use these

And Now:

1. Ubuntu can see four partitions (3 NTFS and 1 ext4) in my computer

2. Windows can just see it-self

Looking for your reply men, thank you very much

Ryan Toss

---

### Post by Ryantoss on 2009-12-05
It seems to be so many threads in this box. So once again, anybody have ideas for my problem. Thank you so much

Ryan

---

### Post by garvinrick4 on 2009-12-05
What does Code:  "sudo fdisk -l"   Without qoutes say. 

That is a small L not an i.

Post the results.

---

### Post by Ryantoss on 2009-12-05
> **garvinrick4 said:**
> What does Code:  "sudo fdisk -l"   Without qoutes say. 

That is a small L not an i.

Post the results.

Here it is man, please feel free to help me T_T

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfd8cfd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9729    62790052+   f  W95 Ext'd (LBA)
/dev/sda5            1913        2942     8273443+  83  Linux
/dev/sda6            2943        5099    17326071   82  Linux swap / Solaris
/dev/sda7            5100        7747    21270028+   7  HPFS/NTFS
/dev/sda8            7748        9449    13671283+   7  HPFS/NTFS
/dev/sda9            9450        9729     2249068+  82  Linux swap / Solaris

---

### Post by garvinrick4 on 2009-12-06
I am sorry I do not know why sda7 and sda8 are NTFS when they like to be
primary around sda2 and sda3 and they look like they are in a extended partition
that the linux partitions and swaps are located. To me it looks like quite a mess.
Maybe someone else will know how to fix this. I cannot.

---

