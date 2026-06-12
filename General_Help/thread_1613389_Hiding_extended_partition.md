---
title: "Hiding extended partition"
date: 2010-11-04
forum: General Help
---

### Post by grumpy.biatch on 2010-11-04
Hi,

I've several operating systems installed on my box, I tried to add Scientific Linux on sdc 12 & 13. It is RHEL based and uses anaconda installer. After allocating partitions the install failed and anaconda went to debug. It has >sdX15 restriction. 

I googled a bit and discovered that if I hide sub partitions under extended partitions on sda I may be able to install Sc-Linux on sdc. 

I boot my machine with SUSE GRUB.

Here is my fdisk 
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007d4a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5874    47182873+   7  HPFS/NTFS
/dev/sda2   *       12402       38913   212957609+   5  Extended
/dev/sda3            5875       10443    36700492+  a5  FreeBSD
/dev/sda4           10444       12401    15727288+  bf  Solaris
/dev/sda5           12402       12923     4192933+  82  Linux swap / Solaris
/dev/sda6           12924       14228    10482381   83  Linux
/dev/sda7           14229       14881     5245191   83  Linux
/dev/sda8           14882       15926     8388229+  83  Linux
/dev/sda9           15926       16578     5242576+  83  Linux
/dev/sda10          16579       17492     7341673+  83  Linux
/dev/sda11          17493       18145     5245191   83  Linux
/dev/sda12          18146       19190     8393931   83  Linux
/dev/sda13          19191       19843     5245191   83  Linux
/dev/sda14          19844       21410    12586896   83  Linux
/dev/sda15          21411       22063     5245191   83  Linux
/dev/sda16          22064       23107     8385898+  83  Linux
/dev/sda17          23108       23760     5245191   83  Linux
/dev/sda18          23761       25327    12586896   83  Linux
/dev/sda19          25328       25393      530113+  83  Linux
/dev/sda20          25394       26307     7341673+  83  Linux
/dev/sda21          26308       26568     2096451   83  Linux
/dev/sda22          26569       27221     5245191   83  Linux
/dev/sda23          27222       28262     8361801   83  Linux
/dev/sda24          28263       28915     5245191   83  Linux
/dev/sda25          28916       30873    15727603+  83  Linux
/dev/sda26          30874       31526     5245191   83  Linux
/dev/sda27          31527       32831    10482381   83  Linux
/dev/sda28          32832       33484     5245191   83  Linux
/dev/sda29          33485       34398     7341673+  83  Linux
/dev/sda30          34399       35051     5245191   83  Linux
/dev/sda31          35052       36095     8385898+  83  Linux
/dev/sda32          36096       36748     5245191   83  Linux
/dev/sda33          36749       37662     7341673+  83  Linux
/dev/sda34          37663       38054     3148708+  83  Linux
/dev/sda35          38055       38707     5245191   83  Linux
/dev/sda36          38708       38838     1052226   83  Linux
/dev/sda37          38839       38913      602406   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007f33d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4569    36699736+  a5  FreeBSD
Partition 1 does not end on cylinder boundary.
/dev/sdc2           14539       57617   346032067+  83  Linux
/dev/sdc3            4570       14538    80075992+   5  Extended
/dev/sdc4           57618      121601   513951480   83  Linux
/dev/sdc5            4570        5483     7341673+  83  Linux
/dev/sdc6            5484        6005     4192933+  83  Linux
/dev/sdc7            6006        8683    21511003+  83  Linux
/dev/sdc8            8684        9466     6289416   83  Linux
/dev/sdc9            9467        9858     3148708+  83  Linux
/dev/sdc10           9859       10772     7341673+  83  Linux
/dev/sdc11          10773       11294     4192933+  83  Linux
/dev/sdc12          11295       12600    10490413+  83  Linux
/dev/sdc13          12601       13122     4192933+  83  Linux
/dev/sdc14          13123       14166     8385898+  83  Linux
/dev/sdc15          14167       14538     2988058+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bb0c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS
```

Menu.lst
```
# Modified by YaST2. Last modification on Tue Nov  2 17:53:58 SGT 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 20
##YaST - generic_mbr
gfxmenu (hd0,30)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.2 - 2.6.31.14-0.4
    root (hd0,30)
    kernel /boot/vmlinuz-2.6.31.14-0.4-desktop  root=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part31 repair=1  resume=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part5 splash=silent  quiet showopts vga=0x317
    initrd /boot/initrd-2.6.31.14-0.4-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2 - 2.6.31.14-0.4
    root (hd0,30)
    kernel /boot/vmlinuz-2.6.31.14-0.4-desktop  root=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part31 showopts apm=off  noresume edd=off powersaved=off nohz=off highres=off  processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.31.14-0.4-desktop

###Don't change this comment - YaST2 identifier: Original name: other###
title Windows 7 Ultimate Edition x64
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: other###
title FreeBSD 8.1 i386
    rootnoverify (hd2,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: other###
title PC-BSD amd64
    rootnoverify (hd0,2)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: other###
title OpenSolaris 2009.06 b134 x86
    rootnoverify (hd0,3)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: other###
title CentOS-base (2.6.18-194.el5) (on /dev/sda6)
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.18-194.el5 ro root=/dev/sda6 rhgb quiet
    initrd /boot/initrd-2.6.18-194.el5.img

###Don't change this comment - YaST2 identifier: Original name: other###
title PCLinuxOS 
    root (hd0,7)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: other###
title Simply Mepis
    root (hd0,9)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: other###
title Chakra Linux
    root (hd0,11)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: other###
title Fedora 13 x86_64
    root (hd0,13)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: other###
title Mandriva Spring 2010.1 x86_64
    root (hd0,15)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: other###
title Calculate Linux x86_64
    root (hd0,17)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: other###
title Arch Linux
    root (hd0,18)
    configfile /grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: other###
title openSUSE 11.3 x86_64
    root (hd0,22)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: other###
title caeLinux amd64
    root (hd0,24)
    kernel /vmlinuz root=/dev/sda25 ro quiet splash
    initrd /initrd.img

###Don't change this comment - YaST2 identifier: Original name: other###
title Ubuntu Studio 10.04 amd64
    root (hd0,26)
    kernel /vmlinuz root=/dev/sda27 ro quiet splash
    initrd /initrd.img

###Don't change this comment - YaST2 identifier: Original name: other###
title Linux Mint 9 amd64
    root (hd0,28)
    kernel /vmlinuz root=/dev/sda29 ro quiet splash
    initrd /initrd.img

###Don't change this comment - YaST2 identifier: Original name: other###
title Debian 506 amd64
    root (hd2,4)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: menu###
title Gentoo Linux 2.6.34-gentoo-r12
    root (hd2,6)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: other###
title Kubuntu amd64 10.10
    root (hd0,34)
    kernel /vmlinuz root=/dev/sda35 ro quiet splash
    initrd /initrd.img

###Don't change this comment - YaST2 identifier: Original name: other###
title Slackware64-13.1
    root (hd0,32)
    kernel /boot/vmlinuz root=/dev/sda33
    boot

###Don't change this comment - YaST2 identifier: Original name: other###
title Salix
    root (hd2,7)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: other###
title vector Linux 6.0
    root (hd2,13)
    kernel /boot/vmlinuz root=/dev/sdc14
    boot

###Don't change this comment - YaST2 identifier: Original name: other###
title Frugalware-x86_64-1.3
    root (hd2,9)
    kernel /boot/vmlinuz root=/dev/sdc8
    boot
```

Will it be appropriate to hide partitions from menu.lst 

here is a sample -

> 
###Don't change this comment - YaST2 identifier: Original name: other###
title openSUSE 11.3 x86_64
    root (hd0,22)
hide (hd0,22)
hide (hd0,23)
configfile /boot/grub/menu.lst


let me know if it is correct or how it needs to be done.

Best,

David

---

### Post by grumpy.biatch on 2010-11-05
After a long hassle and prompt help from Saikee (Just Linux Mod) I was able to install Scientific Linux 

Here is a brief howto -

We can hide partitions with GRUB CD. There are many advantages of using GRUB CD where you can install GRUB quickly and it will bring the right menu for booting. 

```
grub
``````
geometry (hd0)
```I printed the output for records
```
linux-3s52:/home/david # find / -name stage1
/boot/grub/stage1
/usr/lib/grub/stage1
find: `/home/david/.gvfs': Permission denied 
``````
linux-3s52:/home/david # mkdir grubs
``````
linux-3s52:/home/david # cd grubs
``````
linux-3s52:/home/david/grubs # mkdir iso
``````
linux-3s52:/home/david/grubs # mkdir -p iso/boot/grub
``````
linux-3s52:/home/david/grubs # cp /usr/lib/grub/stage2_eltorito iso/boot/grub
``````
linux-3s52:/home/david/grubs # mkisofs -R -b  boot/grub/stage2_eltorito -no-emul-boot \-boot-load-size 4  -boot-info-table -o grub.iso iso
 I: -input-charset not specified, using utf-8 (detected in locale settings)
Size of boot image is 4 sectors -> No emulation
Total translation table size: 2048
Total rockridge attributes bytes: 760
Total directory bytes: 4576
Path table size(bytes): 34
Max brk space used 22000
235 extents written (0 MB)
```
```
linux-3s52:/home/david/grubs # ls
 grub.iso  iso
```Burned the CD, booted with it and ran following commands

```
 grub> geometry (hd0)
``````
 grub> hide (hd0,1)
``` This is my extended partition

```
grub> hide (hd0,2)
``` This is my PC-BSD partition and it has BSD Slices in it, Anaconda reads them.

```
grub> hide (hd0,3)
``` This is my Solaris partition and anaconda reads it.

```
grub> geometry (hd0)
```  Checked how many slices were visible and it returned 4 with no sub slices.

```
 grub> reboot
```I removed the cd and booted with Scientific Linux DVD in it. This time I was able to install Sc-Linux. I placed its GRUB on its '/'.

Later I rebooted with grub cd in order to unhide the slices.

                                                         ```
grub> unhide (hd01)
``` ```
grub> unhide (hd0,2)
``` ```
 grub> unhide (hd0,3)
``` ```
grub> geometry (hd0)
```  Checked the output with the print from start, everything got listed.

At this stage I reinstalled grub on MBR
                                                         ```
 grub> root (hd0,30)
```                            ```
 grub> setup (hd0)
```I did a reboot and found my gorgeous SUSE Menu there. Added menu section for Sc-Linux and rebooted into it. 

Saikee (the guy who installed 145 OS on his box) helped me accomplish this.

Thanks everyone.

Best,

David

---

