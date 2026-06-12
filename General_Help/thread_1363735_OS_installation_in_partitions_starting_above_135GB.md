---
title: "OS installation in partitions starting above 135GB"
date: 2009-12-24
forum: General Help
---

### Post by mdmill9999 on 2009-12-24
I have a 500 GB hard drive and want to multiboot many OS's. I have created many partitions for this purpose. I can write and use partitions located high in the disk eg 135 thru 500gb...so there is no hardware write problem (48 bit LBA, good bios etc).

**However,** I have found that none of the *following* OS installation cd/dvd 's will **install _and_ boot** to partitions starting above ~135 GB :_linux ubuntu9.10, kubuntu9.10, open suse(most recent distro), XP home (sp1) or XP pro(sp2)._ 

Thus, making use of the entire hard disk, in a multiboot computer is problematical [especially since linux does not allow application installations to secondary partitions...(with XP this is not a problem!)]

Has anyone else seen this limitation , especially with ubuntu/kubuntu.
***Specifically, has any one installed and booted ubuntu on a partition starting above ~135GB?!! [I claim it cannot be done] Any advice? ....Thanks much***

PS: I know how to multiboot, and use GRUB> I have multibooted 8 different OS's in the region from 0 up to 150 GB. And created usable data partitions [fat32,NTSF,and EXT2] in the regions of 150 to 500 GB. but I cannot install OS's in partitions starting above ~135GB!!!

---

### Post by mdmill9999 on 2009-12-24
I have a 500 GB hard drive and want to multiboot many OS's. I have created many partitions for this purpose. I can write and use partitions located high in the disk eg 135 thru 500gb...so there is no hardware write problem (48 bit LBA, good bios etc).

**However,** I have found that none of the *following* OS installation cd/dvd 's will **install _and_ boot** to partitions starting above ~135 GB :_linux ubuntu9.10, kubuntu9.10, open suse(most recent distro), XP home (sp1) or XP pro(sp2)._ 

Thus, making use of the entire hard disk, in a multiboot computer is problematical [especially since linux does not allow application installations to secondary partitions...with XP this is not a problem!]

Has anyone else seen this limitation , especially with ubuntu/kubuntu.
***Specifically, has any one installed and booted ubuntu on a partition starting above ~135GB?!! [I claim it cannot be done] Any advice? ....Thanks much***

PS: I know how to multiboot, and use GRUB> I have multibooted 8 different OS's in the area from 0 up to 150 GB. And created usable data partitions [fat32,NTSF,and EXT2] in the regions of 150 to 500 GB. but I cannot install OS's in partitions starting above ~135GB!!!

---

### Post by running_rabbit07 on 2009-12-24
Ubuntu installs with no problem on large HDDs and has no problems with being in Logical partitions. I have done both. I do know that Windows 7 has rejected me trying to install within Logical.

---

### Post by running_rabbit07 on 2009-12-24
Please do not create multiple threads with the same question.

---

### Post by overdrank on 2009-12-24
Hi and welcome, please do not create multiple threads on the same issue as it can cause confusion. Threads merged.

---

### Post by bruno9779 on 2009-12-24
I have my / on a partition of 80 GB.
/home is on the second partition with 700GB

I had an install of windose but I have got rid of it.

The first install I made on this machine used 500 GB for ubuntu and the rest for W7 (w7 never quite worked for me though)

---

### Post by running_rabbit07 on 2009-12-24
I think the problem the OP is having is due to trying to do the Ubuntu install without the / and /home setup along with swap.

---

### Post by falconindy on 2009-12-24
OP's hardware may be old enough that his/her BIOS is the culprit, not the OS.

---

### Post by louieb on 2009-12-24
> **falconindy said:**
> OP's hardware may be old enough that his/her BIOS is the culprit, not the OS.
Thats my guess too.
From [IDBS GRUB Page]("http://members.iinet.net.au/%7Eherman546/p15.html") 
 > 
The main reason for needing a separate /boot partition is for curing GRUB error 18. 
GRUB error 18 most commonly occurs when a hard disk is larger than the computer's BIOS was designed for. 

                                       Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)


---

### Post by efflandt on 2009-12-24
I have been around long enough that I remember when I could only use 528 MB of a 540 MB drive until I got a card that could allow my system to do LBA.  But that was when you could run X on 8-16 MB.

Just an example of 64-bit Ubuntu 9.10 I added from CD on the tail 22 GB of a 250 GB drive in case the user of this machine trashes Win7 (grub2 is on sda4 with standard mbr on drive):

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75349890

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       27597   206268600    7  HPFS/NTFS
/dev/sda4   *       27598       30401    22523130   83  Linux
```

---

### Post by oldfred on 2009-12-25
On my newish 640GB drive I installed Karmic alpha in partition c7 which started at about 400GB. I did chainboot into grub2 installed in that partition and got grief about blocklists on every update. Have not used it for a while as I now have a clean install but will reuse partition when I decide to test Lucid.

---

### Post by mdmill9999 on 2009-12-29
[Original Poster]-I finally discovered that my Dell 8250 bios a01 had a flaw when (sometimes)writing to large (UDMA) drives above 137GB! A bios flash upgrade to bios a04 solved the problems I was having with installs, as many had suggested. Thanks to all for the responces and to efflandt and oldfred for their specific examples (which got me re-thinking!)

---

