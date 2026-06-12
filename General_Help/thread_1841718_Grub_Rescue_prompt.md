---
title: "Grub Rescue prompt"
date: 2011-09-09
forum: General Help
---

### Post by 66traveler on 2011-09-09
I have this X86 machine, running Windows, with which I took the plunge into Feisty. A couple of years with dual boot and learning the ways of Ubuntu. Later, I added to the box a used drive that just sat there until I upgraded to Karmic.  The install did not overwrite Feisty but Grub did pick up the secondary HDD.  Things are good until I decide to reformat the secondary drive as a plan to moving Windows to it's own drive.

I used the Ubuntu system tools and when it asked about the clearing the partition table I said OK.

Now, the boot hangs at
```
verifying DMI Pool Data error: no such device
8elfccf6-20bb-46f6-9bf8-78393dafcae06
Grub rescue>
```

Over the course of several months I have tried to remedy this by reading and trying many approaches which were not necessarily titled to deal with exactly this error state.  The related threads that I have followed have focused on recovering or reinstalling Grub from the Live CD or using the Super Grub Disc utilities.  No success.

Additionally, I have downloaded from SourceForge.net a Boot Info Script and have generated much more info than I do fully understand.  None the less, I have gained much understanding.

I would like to ask the forum specifically about the re-installation approach from the Live CD.

Using a magazine distributed Karmic Live CD, I was successful in following a set of forum posted instruction until I tried to execute: ```
grub-install /dev/sda
```

It returned:
```
cp:reading '/usr/lib/grub/i386-pc/elf.mod':
Input/output error
```

I have a couple of theories about why this might have come about but am less sure as to how I might approach a solution.

Please advise.

---

### Post by YesWeCan on 2011-09-10
How about posting the bootinfoscript RESULTS.txt?

---

### Post by raja.genupula on 2011-09-10
> **66traveler said:**
> I have this X86 machine, running Windows, with which I took the plunge into Feisty. A couple of years with dual boot and learning the ways of Ubuntu. Later, I added to the box a used drive that just sat there until I upgraded to Karmic.  The install did not overwrite Feisty but Grub did pick up the secondary HDD.  Things are good until I decide to reformat the secondary drive as a plan to moving Windows to it's own drive.

I used the Ubuntu system tools and when it asked about the clearing the partition table I said OK.

Now, the boot hangs at
```
verifying DMI Pool Data error: no such device
8elfccf6-20bb-46f6-9bf8-78393dafcae06
Grub rescue>
```

Over the course of several months I have tried to remedy this by reading and trying many approaches which were not necessarily titled to deal with exactly this error state.  The related threads that I have followed have focused on recovering or reinstalling Grub from the Live CD or using the Super Grub Disc utilities.  No success.

Additionally, I have downloaded from SourceForge.net a Boot Info Script and have generated much more info than I do fully understand.  None the less, I have gained much understanding.

I would like to ask the forum specifically about the re-installation approach from the Live CD.

Using a magazine distributed Karmic Live CD, I was successful in following a set of forum posted instruction until I tried to execute: ```
grub-install /dev/sda
```

It returned:
```
cp:reading '/usr/lib/grub/i386-pc/elf.mod':
Input/output error
```

I have a couple of theories about why this might have come about but am less sure as to how I might approach a solution.

Please advise.

```
sudo os-prober 
```
for detecting where you have installed your OS know and what  they are .

go with this 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by 66traveler on 2011-09-11
YesWeCan;

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.04
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   130,994,009   130,993,947   c W95 FAT32 (LBA)
/dev/sda2         130,994,010   230,115,059    99,121,050  83 Linux
/dev/sda3         230,115,121   234,436,544     4,321,424   5 Extended
/dev/sda5         230,115,123   234,436,544     4,321,422  82 Linux swap / Solaris

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  38     7,839,719     7,839,682   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        251F-19EC                              vfat       
/dev/sda2        440d0713-7329-4bb3-b4b7-36e8a55bf62b   ext3       
/dev/sda5        753fc288-cd90-4202-897b-7282dce8577b   swap       
/dev/sdc1        D803-D8C1                              vfat       Cruzer

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/Cruzer            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

--------------------------------------------------------------------------------

=========================== sda2/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=440d0713-7329-4bb3-b4b7-36e8a55bf62b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=440d0713-7329-4bb3-b4b7-36e8a55bf62b ro quiet splash
initrd		/boot/initrd.img-2.6.20-17-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=440d0713-7329-4bb3-b4b7-36e8a55bf62b ro single
initrd		/boot/initrd.img-2.6.20-17-generic

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=440d0713-7329-4bb3-b4b7-36e8a55bf62b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=440d0713-7329-4bb3-b4b7-36e8a55bf62b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=440d0713-7329-4bb3-b4b7-36e8a55bf62b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=440d0713-7329-4bb3-b4b7-36e8a55bf62b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=440d0713-7329-4bb3-b4b7-36e8a55bf62b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=753fc288-cd90-4202-897b-7282dce8577b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  71.726368904 = 77.015602176   boot/grub/menu.lst                             1
  71.736355782 = 77.026325504   boot/grub/stage2                               2
  71.836670876 = 77.134038016   boot/initrd.img-2.6.20-15-generic              3
  71.759499550 = 77.051175936   boot/initrd.img-2.6.20-15-generic.bak          3
  71.845093727 = 77.143081984   boot/initrd.img-2.6.20-16-generic              4
  71.774743080 = 77.067543552   boot/initrd.img-2.6.20-16-generic.bak          4
  71.797402382 = 77.091873792   boot/initrd.img-2.6.20-17-generic              3
  71.789601326 = 77.083497472   boot/initrd.img-2.6.20-17-generic.bak          3
  71.761227608 = 77.053031424   boot/vmlinuz-2.6.20-15-generic                 2
  71.722340584 = 77.011276800   boot/vmlinuz-2.6.20-16-generic                 2
  71.725209236 = 77.014356992   boot/vmlinuz-2.6.20-17-generic                 2
  71.797402382 = 77.091873792   initrd.img                                     3
  71.845093727 = 77.143081984   initrd.img.old                                 4
  71.725209236 = 77.014356992   vmlinuz                                        2
  71.722340584 = 77.011276800   vmlinuz.old                                    2

```

raja.genupula;
  I trust that the results.txt will contain the information that the os-prober would reveal.
  The link to the Ubuntu Documentation page I read some months back but was hesitant to pursue because of the "after installing windows".  Now that I look at it again some of the approaches are not so intimidating.

  I will update this thread after I have tried a few things.
  Thanks.

---

### Post by raja.genupula on 2011-09-11
hey 66traveler , you loss nothing ,it simply gonna restore your grub .

---

### Post by YesWeCan on 2011-09-11
Bootinfoscript shows two problems:
1) The MBR grub code is looking in sda5 for / but / is in sda2
2) The MBR grub code is Grub-2 but the grub files in sda2 are Grub-1

Do you want to get 7.04 booting again off the sda drive or do you want to do something else involving the sdb drive?

To get 7.04 booting, I'd recommend using the chroot method to reinstall a Grub-1 boot program to the MBR area of sda. This method is described here [https://help.ubuntu.com/community/Grub2#](https://help.ubuntu.com/community/Grub2#) (intended for grub2 but will work for grub1).

You say you have already tried some methods and they failed. Did you try this method? If you tried this and it failed you may need to purge grub and reinstall it too.


Alternatively, if you want to upgrade your Ubuntu you could install a more recent version on sdb that has Grub2 and it will add your 7.04 and XP on sda to its boot menu.

---

### Post by 66traveler on 2011-09-11
raja.genupula,
  I usually work on the problem in the evenings and thus the delays.  I will make sure to close the thread when complete.

YesWeCan,
  I checked into the link regarding Grub-2. I had dismissed it earlier since it seemed to deal with a version that I did not have. But apparently it came with Karmic. Upon reading there is a good explanation of the differences and compatibilities. A big help.
  I have little interest in preserving 7.04 and would like it deleted. I intend to restore or reinstall 10.04. So I should at least update to Grub-2.
  As I recall I patiently tried a chroot process but was unsuccessful. I may have had the syntax wrong or something but did make several attempts. I'll keep reading the link you provided and see if I can get something to work.
  At this point, moving the windows to sdb was my original intent. I would like to install a newer version of Ubuntu to the sda drive since it is the larger one and I rarely boot to windows anyway.
  Would a drive image transfer (parted-magic?) leave things intact enough to then allow the install with grub-2 to audit the whole system?  Or, it this too ambitious? 
  Some of my reading included an excellent posting by Herman that included a link to a page titled "Illustrated Dual Boot Site".  There was a mention of problems but they seemed to deal with placing grub in it's own partition.  I need to review the information before proceeding with this idea.
  Thank you for the feedback.
  More later.

---

### Post by 66traveler on 2011-09-12
Later,
  Tried the Boot-Repair path.
  1st time, Synaptic had no record. Approached issue through terminal that did not generate menu item in System>Admin but did generate listing in Synaptic. Ran install in Synaptic and found menu item now in >Admin.  Ran Boot-Repair all the way through and reboot with same device error/grub rescue prompt.
  2nd time, started installing Boot-Repair in terminal like last time. Entire process opened in separate window and ran in sync with the line items viewed concurrently in the still open terminal. Restarted the machine and got same error message with grub rescue prompt.
  Tried the upgrade to Grub-2 approach.
  Still using the Karmic Live CD, used terminal commands since the  aforementioned Boot-Repair window did not match the one shown in the Community Documentation. Noticed lots of "Lucid" attached the incoming files. I did get grub-pc to install but could not find it.
  More tomorrow.

---

### Post by 66traveler on 2011-10-11
4 weeks later,
In the mean time, I worked with the 10.04 live CD to try to install Grub2 without success.
Next I detoured into Gparted to do some maintenance on the drives including a newly installed external into which I intend to Partimage the surviving partitions' data.
More reading.

Last night,
After considering raja.genupula's post I felt that he was suggesting that a solution to my problem was easier than I realized.  
I decided to boot to my copy of the V0.97 Super Grub Disc and then start Feisty in the uncorrupted sda2.  From there I intended to try a reinstall of Grub.

In Grub, I selected the GNU, Linux with Help. After two successive menu options resulting in positive responses, the process was ready for removal of the disc and a restart.  The SGD ran the whole process.

Grub selection screen appeared and allowed a successful boot into Feisty.  Nice.  A long way around to this result but satisfied with the trip.

Thanks once again to Raja.genupula and YesWeCan for their answers to my call for advice.

---

