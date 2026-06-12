---
title: "GRUB help! 3 OS'es and 4 hdds."
date: 2009-08-02
forum: General Help
---

### Post by Tattys on 2009-08-02
So I have finally caved after countless attempts. I am trying to add my XP partition (sda1) to grub. Here is my fdisk -l

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x358e358d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       21035   107523045    7  HPFS/NTFS
/dev/sda3           28613       38913    82742782+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00046422

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x757e757e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdc2           12749       30394   141741495   83  Linux
/dev/sdc3           30395       38540    65432745   83  Linux
/dev/sdc4           38541       38913     2996122+  82  Linux swap / Solaris

Disk /dev/sdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13141314

   Device Boot      Start         End      Blocks   Id  System
 
```Grub is on sdc, and ubuntu is sdc2, whereas sdc1 is win7. And XP is sda1 which I want to add. I've tried (hd0,0) but it gives me the win7 partition, which I thought should be (hd2,0).

```

title        Windows 7 RC 7100 x64
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```I've tried...
(hd1,0): no such partition.
(hd2,0): starting up...disk read error
(hd3,0): starting up...BOOTMGR is missing

Another thing, I can get into XP, I just have to rearrange the hdd order in the BIOS. Currently sdc (ubunut/win7) is IDE channel 0 master and XP is channel 2 master. So shouldn't (hd2,0) be where the XP partition is?? If so, how do I access it?? What am I not noticing?! Thx.

---

### Post by SoftwareExplorer on 2009-08-03
> **Tattys said:**
>  I've tried (hd0,0) but it gives me the win7 partition, which I thought should be (hd2,0).

...

Another thing, I can get into XP, I just have to rearrange the hdd order in the BIOS. Currently sdc (ubunut/win7) is IDE channel 0 master and XP is channel 2 master. So shouldn't (hd2,0) be where the XP partition is?? If so, how do I access it?? What am I not noticing?! Thx.

When you tried hd0,0 did you have your hard drives re-ordered in the bios? My guess it when you re-order in the bios it switches channels and that makes hd0 become hd2 and vice versa. Maybe that's what's causing problems?  Are the hard disks Sata or EIDE? Sata is a cable that is flat and about 1 cm across. Eide is about an inch and a half where it connects.

---

### Post by SoftwareExplorer on 2009-08-03
I almost forgot. Welcome to Ubuntu forums, Tattys.

---

### Post by Tattys on 2009-08-04
Thank you for the welcoming! I've been an avid reader for awhile now, but finally joined.

Anyways, the WinXP (sda) is IDE and the other (sdc) is SATA. Now I got all the information when I had the bios boot setup as IDE 1st and SATA 2nd. This is how I get into Ubuntu.
Whenever I need to get into XP, I just flip the order, so SATA 1st and IDE 2nd. 
It doesn't make sense to me though, I thought it would be the reverse, because each hard drive has its own boot loader and FIFO.

---

### Post by SoftwareExplorer on 2009-08-04
do you mind running ```
sudo blkid
```? It will make a partition identifier that stays the same no matter whether it is sda6 or sdc6. I think if we set grub to identify partitions that way it wont matter as much what order they are in.

---

### Post by SoftwareExplorer on 2009-08-04
And if you can, when you run the command tell what OSes are currently on it. It would also help if you could tell me what kernels your ubuntu has. You could run ```
ls /boot
``` to give me an idea.

---

### Post by Tattys on 2009-08-05
Sorry for the delay,
here's the blkid...
```

/dev/sda1: UUID="161CD93E1CD91997" LABEL="XP" TYPE="ntfs" 
/dev/sda2: UUID="0D170CBC5B9EA1A0" LABEL="storage" TYPE="ntfs" 
/dev/sdb1: UUID="4525F02F614F3A6B" TYPE="ntfs" LABEL="storage" 
/dev/sda3: UUID="02B14B8B0D51F60D" LABEL="games" TYPE="ntfs" 
/dev/sdc1: UUID="7F24964F463ED0BE" LABEL="win7" TYPE="ntfs" 
/dev/sdc2: UUID="d7344bd2-ae62-42f9-9885-7b9eb950ce5d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="d9cda045-7223-487b-94ab-23c682285f7f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc4: TYPE="swap" UUID="fc21fa2b-4654-4a77-b024-a2c47b31a2e9" 

```and the kernels...
```

abi-2.6.28-11-generic     config-2.6.28-14-generic      memtest86+.bin                vmcoreinfo-2.6.28-13-generic
abi-2.6.28-13-generic     grub                          System.map-2.6.28-11-generic  vmcoreinfo-2.6.28-14-generic
abi-2.6.28-14-generic     initrd.img-2.6.28-11-generic  System.map-2.6.28-13-generic  vmlinuz-2.6.28-11-generic
config-2.6.28-11-generic  initrd.img-2.6.28-13-generic  System.map-2.6.28-14-generic  vmlinuz-2.6.28-13-generic
config-2.6.28-13-generic  initrd.img-2.6.28-14-generic  vmcoreinfo-2.6.28-11-generic  vmlinuz-2.6.28-14-generic


```

---

### Post by SoftwareExplorer on 2009-08-06
Backup your current menu.lst. ```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
``````
sudo gedit
```Paste this in:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d7344bd2-ae62-42f9-9885-7b9eb950ce5d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d7344bd2-ae62-42f9-9885-7b9eb950ce5d

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false


title           Linux:
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        d7344bd2-ae62-42f9-9885-7b9eb950ce5d
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=d7344bd2-ae62-42f9-9885-7b9eb950ce5d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        d7344bd2-ae62-42f9-9885-7b9eb950ce5d
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=d7344bd2-ae62-42f9-9885-7b9eb950ce5d ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        d7344bd2-ae62-42f9-9885-7b9eb950ce5d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d7344bd2-ae62-42f9-9885-7b9eb950ce5d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        d7344bd2-ae62-42f9-9885-7b9eb950ce5d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d7344bd2-ae62-42f9-9885-7b9eb950ce5d ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d7344bd2-ae62-42f9-9885-7b9eb950ce5d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d7344bd2-ae62-42f9-9885-7b9eb950ce5d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d7344bd2-ae62-42f9-9885-7b9eb950ce5d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d7344bd2-ae62-42f9-9885-7b9eb950ce5d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d7344bd2-ae62-42f9-9885-7b9eb950ce5d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows:

title           Windows 7 RC 7100 x64
uuid            7F24964F463ED0BE
savedefault
makeactive
chainloader     +1

title           Windows XP
uuid            161CD93E1CD91997
savedefault
makeactive
chainloader     +1
```Save it as /boot/grub/menu.lst.
Run ```
sudo update-grub
``` to apply the changes.

---

### Post by Tattys on 2009-08-06
All done.

I tried the two windows entries but received "Error 15: File Not Found" for both. 
I just restored the backup now.

---

### Post by martinbaselier on 2009-08-06
You can find the correct commands when you press c to enter the commandline in grub while booting. You might need to press esc first to get into the menu. 

then

root (hd0,0) 
chainloader +1
boot

(you can use tab for autocomplete and to show available options)

you can experiment with the root command. It will change the partition. 
If you've found the correct location, you can change /boot/grub/menu.lst

If you run update-grub it will remove all manual changes you made and automatically generate /boot/grub/menu.lst

---

### Post by P4man on 2009-08-06
AFAIk, Windows won't boot from anything but the first drive. if you change boot order in bios, you make the windows drive the first one, and its happy. When you boot from the other drive which has grub, the windows drive is no longer the first one and windows bootloader balks.

So try this:

title Windows
    map (hd0) (hd1)
    map (hd1) (hd0)
    rootnoverify (hd0,0)
    chainloader +1
    makeactive

It will swap drive 0 and 1 so that windows thinks its booting from the first drive again.

---

### Post by Tattys on 2009-08-06
hmm so I've tried the mapping but it goes straight to my win7.
Could I rearrange the hard drives so that my XP is first, and then reinstall grub on to the XP drive to locate my ubuntu and win7 partitions??

---

### Post by oldfred on 2009-08-06
I am not sure which drive you now have booting first.
Windows 7 and Vista need [COLOR=DarkRed]rootnoverify[/COLOR] and no [COLOR=DarkRed]makeactive[/COLOR] entries. For XP root or rootnoverify will work if set up correctly. If using the root command for XP then makeactive is required.
For the Windows that is not (hd0,0) your will need the map command as P4man gave you.
If XP is on the first drive:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

If windows 7 is the first drive
title        Windows 7 Ultimate, chainloader (on /dev/sda1)
rootnoverify    (hd0,0)
savedefault
chainloader +1

Add the map command just before the chainloader command and adjust (hd0,0) to (hd2,0) for whichever Windows is your 3rd drive.

map        (hd0) (hd2)
map        (hd2) (hd0)

---

### Post by SoftwareExplorer on 2009-08-06
> **martinbaselier said:**
> 
If you run update-grub it will remove all manual changes you made and automatically generate /boot/grub/menu.lst

So in that case, how would you use a new menu.lst?

Also, with the rootnoverify, how would you use a uuid to boot windows?

---

### Post by oldfred on 2009-08-07
I have not run update-grub or the editor for menu.lst that some recommend. If you use either of these be sure to make a backup of your current menu.lst before running them.
I have never seen a UUID used for a Windows boot, only for Linux.

---

