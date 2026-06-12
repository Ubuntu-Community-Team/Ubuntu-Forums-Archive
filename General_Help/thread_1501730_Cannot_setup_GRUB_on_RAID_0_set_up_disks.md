---
title: "Cannot setup GRUB on RAID 0 set up disks"
date: 2010-06-04
forum: General Help
---

### Post by belnac on 2010-06-04
Hi,

I've been all afternoon trying to install Ubuntu Lucid on my **fake**RAID 0 configured (2) HDDs and am unable to set GRUB up. The fake RAID setup is provided by Intel Matrix Storage Manager, it is correctly enabled and the BIOS is also correctly set up -- in fact, I've managed to install Windows 7 with no significant hitch.

After struggling with partioning the drives (had to follow advice I found on a very helpful guide online [0]), creating the filesystems AND getting Ubuntu's installer to actually do what it is supposed to do, I now cannot seem to set GRUB up. My system, as it stands, is unbootable at all; via live CD only. :-/

This is how the RAID0 dev is partitioned:

```
# fdisk -l /dev/mapper/isw_ecdeiihbfi_Volume0

Disk /dev/mapper/isw_ecdeiihbfi_Volume0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6634b2b5

                              Device Boot      Start         End       Blocks   Id  System
/dev/mapper/isw_ecdeiihbfi_Volume0p1               1          32       249856   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/mapper/isw_ecdeiihbfi_Volume0p2              32       75601    607009537    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_ecdeiihbfi_Volume0p3   *       75601       75614       102400    7  HPFS/NTFS
/dev/mapper/isw_ecdeiihbfi_Volume0p4           75614      101097    204697600    7  HPFS/NTFS
/dev/mapper/isw_ecdeiihbfi_Volume0p5              32         281      1999872   82  Linux swap / Solaris
/dev/mapper/isw_ecdeiihbfi_Volume0p6             281       12730     99999744   83  Linux
/dev/mapper/isw_ecdeiihbfi_Volume0p7           12730       13354      5009408   83  Linux
/dev/mapper/isw_ecdeiihbfi_Volume0p8           13354       75601    499999744   83  Linux
```Note: /dev/mapper/isw_ecdeiihbfi_Volume0p1 is where /boot is mounted.

Having read a few posts and guides I found here and there [0][1][2], I started by removing grub and reinstalling it from scratch like so (after chrooting into the filesystem):

```
# apt-get purge grub2 grub-pc grub
# rm -rf /boot/grub
# mkdir /boot/grub
# apt-get install grub
```Here's when it starts playing up:

```
# grub-install /dev/mapper/isw_ecdeiihbfi_Volume0
/dev/mapper/isw_ecdeiihbfi_Volume0 does not have any corresponding BIOS drive.
```Nothing is copied to /boot/grub. Only device.map is created. So,

```
# cp /usr/lib/grub/x86_64-pc/* /boot/grub

# cat /boot/grub/device.map
(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
```Clearly wrong; edited device.map in nano.

```
# cat /boot/grub/device.map
(fd0)    /dev/fd0
(hd0)    /dev/mapper/isw_ecdeiihbfi_Volume0
```Now I tried setting up grub:

```
# grub --no-curses

grub> device (hd0) /dev/mapper/isw_ecdeiihbfi_Volume0
device (hd0) /dev/mapper/isw_ecdeiihbfi_Volume0
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
```...and kaboom! I lose, game over.

In desperation I went ahead and tried setting it up in hd0,0 (commands root (hd0,0) && setup (hd0) ) but no luck.

I am really at a complete loss here. I don't know what else to do and would very much appreciate some help. This has been a very frustrating experience so far full obstacles that never seem to go away no matter how many posts, guides or how-to tutorials I read. :-|



[0] [https://help.ubuntu.com/community/FakeRaidHowto#Preconfigure%20the%20New%20System](https://help.ubuntu.com/community/FakeRaidHowto#Preconfigure%20the%20New%20System)
[1] [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)
[2] [http://ubuntuforums.org/showpost.php?p=8643812&postcount=40](http://ubuntuforums.org/showpost.php?p=8643812&postcount=40)

---

### Post by belnac on 2010-06-05
Replying to my own question as I found the solution roughly 5 minutes after posting it and thought it might be of help to anyone facing the same issue as I was.

It turns out the guides/posts I found were mostly right in almost every single way. I did have to make adjustments along the way -- i.e. use different tools at different steps like when creating the filesystems -- but the general direction described in them was spot on and allowed me to finally, after so much frustration, partition my RAID0 enabled disks, create the filesystems and install Ubuntu Lucid.

I was failing to install and set GRUB up because apparently neither of the authors of the posts/guides had created a partition for [FONT="Courier"]/boot[/FONT] whereas I had, along with [FONT="courier"]/home[/FONT]. As such, their guides only described chrooting into a root-centric filesystem (no [FONT="courier"]/boot[/FONT] or any other partitions.) So, whenever I chrooted into my filesystem from the Live CD without first mounting my [FONT="courier"]/boot[/FONT] partition, running whatever GRUB commands was **not** affecting my [FONT="courier"]/boot[/FONT] partition.

As such, the solution is obvious enough: I only had to mount my [FONT="courier"]/boot[/FONT] _before_ chrooting into my filesystem. Then it was only a matter of running the GRUB commands described in my OP and, voila, Ubuntu lives in RAID 0! I've even been able to install Windows, the 7th and dualboot! Just awesome.

One note though. Running [FONT="courier"]find /boot/grub/stage1[/FONT] still didn't work for me so I had to guess what parameters to pass to [FONT="courier"]root (hdx,y)[/FONT]. It turns out that in my case [FONT="Courier"](hd0,0)[/FONT] were the right parameters to pass as is in my OP but your mileage may vary (reason for my guess was [FONT="courier"]/boot[/FONT] was the first partition I created before anything else.)

So, all this hassle because of a newbie mistake! 

I really hope this may be of help to anyone out there as much as I found the posts/guides referenced in my OP helpful.

---

