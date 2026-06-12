---
title: "Partition table + Gparted problem"
date: 2010-09-17
forum: General Help
---

### Post by Chikitulfo on 2010-09-17
Hi,
I have a laptop with a 320GB disk. Windows 7 and Ubuntu 10.04
It has 8 partitions:
[From Testdisk]
```
 1 * HPFS - NTFS              0  32 33  1530 205 19   24590336 [Recovery]
 2 P HPFS - NTFS           1530 205 20  1543 141  6     204800 [System Reserved]
 3 P HPFS - NTFS           1543 141  7 13903 254 63  198570576
 4 E extended LBA         13904   0  1 38913 254 63  401785650
 5 L HPFS - NTFS          13905   1  1 20170 254 53  100663217 [Datos]
   X extended             20171   0  1 35550 254 58  247079695
 6 L Linux                20171   1  1 35550 254 58  247079632 [ext4Part]
   X extended             35551   0  1 35799 254 45    4000167
 7 L Linux Swap           35551   1  1 35799 254 45    4000104
   X extended             35800 254  1 38912 254 63   49994343
 8 L Linux                35801   0  1 38912 254 63   49994280

```
First two already came with the laptop; 3 is Windows 7; 5 and 6 are 2 data partitons in ntfs and ext4 respectively; 7 is the swap and 8 is Ubuntu.

Long story short, after reinstalling windows 7 and messing around a little with its partition and the other ntfs one (resizing etc); Gparted won't open the disk. It shows all the disk as unallocated space, And throws a message to the terminal which says something like "Can't have a partition out of the disk."

Funny thing is that *almost* everything is working fine. Everything works except that ubuntu can't use the swap. (Dmesg says: "Swap area shorter than signature indicates")

Also, testdisk, if i run a deep search for partitions, finds the last partition twice, but the second time the partition goes from 37129   0  1 to 40240 254 63 , while the disk ends at 38913 255 63.

The problem is that I can't use Gparted now and I want to resize a partition.Also I believe that going without swap is not good for ubuntu.

So if someone could help me find a solution I'd be really grateful.

Thanks in advance.

PS:Attached you can find testdisk log

---

### Post by srs5694 on 2010-09-17
See [this Web page of mine](http://www.rodsbooks.com/missing-parts/index.html) on the topic. I can't be 100% sure that you're seeing the same thing, but you probably are. If you need more advice, please post the output of "sudo fdisk -lu", preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

### Post by Chikitulfo on 2010-09-17
Yep, the problem with Gparted was exactly the one you point in there.

Although I have further problems (still the one about the swap...). I can start resizing partitions with Gparted as I wanted to do.

Thanks!

---

