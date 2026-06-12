---
title: "Mount NTFS files system to repair windows system32"
date: 2010-03-30
forum: General Help
---

### Post by abycons on 2010-03-30
I was follooing this instructions to repair windows system32 in 
this tutorial found in a previus tread, my laptop is Dell xps 2010 I had Ubuntu Live cd running with Internet,mouse and keyboard, 
The NTFS and NTFSProgs  exist in System/ administration /synatip Package Manager,but i can mount the filesystem properly due the device name etc,thing i missing some code in terminal application.

This is the tread...
The steps below are how I fixed the problem! 

[LIST]
[*]**Install NTFS-3G**[INDENT]This package allows you to perform I/O on an NTFS filesystem.[/INDENT]
[*]**Install NTFSProgs**[INDENT]This package contains some useful admin tools to use on NTFS filesystems[/INDENT]
[*]**Mount NTFS filesystem**[INDENT]You will need to mount your Windows partition to backup your corrupted registry files. To do this run the following commands[INDENT]<b>sudo mkdir /media/windows
sudo ntfs-3g -o rw /dev/<device-name> /media/windows[INDENT]if you get a message regarding Windows not being shutdown properly, then run the following command to force the mount[/INDENT]sudo ntfs-3g -o force,rw /dev/<device-name> /media/windows

Both of the above commands will mount the device as read-write.
</b>[/INDENT][/INDENT]
[*]**Replace these files**[INDENT]**[COLOR=Red]You might want to back up the files in /media/windows/WINDOWS/system32/config/ before replacing them just in case this is not a registry problem[/COLOR]**[/INDENT][INDENT]Now copy the following files from the file **/media/windows/System Volume Information/_restore{xxx}/RPxxx/snapeshot/** dir:[INDENT]
_REGISTRY_USER_.DEFAULT
_REGISTRY_MACHINE_SECURITY
_REGISTRY_MACHINE_SOFTWARE
_REGISTRY_MACHINE_SYSTEM
_REGISTRY_MACHINE_SAM
[/INDENT]to the **/media/windows/WINDOWS/system32/config/** dir and name them as follows:[INDENT]
_REGISTRY_USER_.DEFAULT            =>  default
_REGISTRY_MACHINE_SECURITY     =>  security
_REGISTRY_MACHINE_SOFTWARE   =>  software
_REGISTRY_MACHINE_SYSTEM         =>  system
_REGISTRY_MACHINE_SAM               =>  sam
[/INDENT][/INDENT]
[*]**Schedule a consistency check**[INDENT]Run this command to schedule a NTFS consistency check for the first boot into Windows[INDENT]** sudo ntfsfix /dev/<device-name>**[/INDENT][/INDENT]
[*]**Reboot into Windows twice**[INDENT] The first reboot you should get a blue screen telling you that you should run a filesystem consistency check. Let the check run and then the second reboot should bring you back into a bootable Windows[/INDENT]
[*]end of this tread.
[/LIST]
And this is what i had when i run this code...



ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   220492188   224685089     2096451    c  W95 FAT32 (LBA)
/dev/sda2          144585   220476059   110165737+   7  HPFS/NTFS
/dev/sda3       220492125   224685089     2096482+   f  W95 Ext'd (LBA)
/dev/sda4       224685090   234420479     4867695   db  CP/M / CTOS / ...
/dev/sda5   *   220492188   224685089     2096451    0  Empty

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *   220492188   224685089     2096451    c  W95 FAT32 (LBA)
/dev/sdb2          144585   220476059   110165737+   7  HPFS/NTFS
/dev/sdb3       220492125   224685089     2096482+   f  W95 Ext'd (LBA)
/dev/sdb4       224685090   234420479     4867695   db  CP/M / CTOS / ...
/dev/sdb5   *   220492188   224685089     2096451    0  Empty

Partition table entries are not in disk order.

Regard the repair of windows media center edition (windows system32 corrupted...).
Thanks for your help.
Im very confused about where to go in the next step
Aby
Boston MA

---

### Post by uRock on 2010-03-30
Is this a HowTo thread or are you asking for help?

Cheers,
Ronnie

---

### Post by abycons on 2010-03-30
Hi, I had windows media edition corrupted in windows system32 i found that tread,the first part ,but did not work for me,for some reason,second part,now  looking for help couse i got very cunfused.the tread is old (2008) perhaps is a better way now,i'm knew to Ubuntu.
thanks 
Aby

---

