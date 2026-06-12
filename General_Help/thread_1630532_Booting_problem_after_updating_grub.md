---
title: "Booting problem after updating grub"
date: 2010-11-25
forum: General Help
---

### Post by yousifmagdi on 2010-11-25
I just updated things, and i think grub is one of them. But when I restarted my computer after the update it didn't boot and give me the message:

```
grub rescue>
```and no other command work rather than ls.

when checking the internet for solutions i found that it's a common problem, and it happens for those who installed linux using wubi.

I tried

```
grub rescue> ls
(hd0) (hd1) (hd2) (fd0)
grub rescue> ls (hd0)/boot
error: unknown filesystem.
grub rescue> ls (hd1)/boot
error: unknown filesystem.
grub rescue> ls (hd2)/boot
error: unknown filesystem.
grub rescue> ls (hd2)/boot
error: fd0 read error.
```please help.

---

### Post by dino99 on 2010-11-25
you get it because it cant find the good path into the boot line (wrong uuid)


grub rescue> sudo blkid
let you know the exact uuids 

and reboot with the good uuid (editing the boot line)

then after booting: sudo update-grub

---

### Post by drs305 on 2010-11-25
You mention wubi - are you using it?  If so, and you don't see a Windows menu first, you probably installed Grub2 onto the MBR. This replaced the Windows bootloader, which must be used with Wubi.

But to prevent guessing, if you can boot an Ubuntu LiveCD and then download and run the boot info script from the following link we can be sure what is happening. Post the contents of the RESULTS.txt file which the script will produce.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by coomdoom on 2010-11-25
Hi,

I'm having the exact same problem as well so I have generated a results.txt as requested. Hopefully what mine has produced would be similar to what the OP would produce if they did it too.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,276,030   488,275,968   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       57dd0932-79f2-4e0c-9051-fbfff56935b6   ext4                                     
/dev/sda1        EA1C24EA1C24B40B                       ntfs       Windows Seven                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        282C556D2C5536D2                       ntfs       Data                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


```

Hope you're able to help as I really need to get into Windows 7 without having to do any sort of Windows reinstall. Also if this helps, I ran my Windows 7 Startup Disk and it ran a test to see if there were startup problems but it did not detect any.

---

### Post by wilee-nilee on 2010-11-25
Good eye drs305;)

@coomdoom down load the recovery link and **run the one command** I highlight just follow the directions. You can also just use a W7 installDVD .
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by drs305 on 2010-11-25
@ coomdoom,


*wilee-nilee* was responding to the original poster, but what he says applies to you as well.

It looks like you also have Grub installed on the MBR of sda. The sda MBR should be 'owned' by Windows, not by Grub2. So you need to reinstall the Windows bootloader. 

You can follow wilee-nilee's instructions to reinstall the Windows bootloader.

If you don't have the disks, he provided you a link to a Windows compatible file. 

I believe you can also do it by installing *lilo* via the LiveCD and then writing to the MBR that way. I'm not a Windows person, and using the Windows disk would be preferable, but I think this will also work - at least it does for XP and Vista:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Don't worry about the lilo messages generated - you don't really want to fully install lilo as the messages want you to do.

---

### Post by coomdoom on 2010-11-25
I was able to make a recovery CD from my laptop which has Windows 7. I followed the instructions for the recovery CD and they worked perfectly. Thank you very much, all your help is greatly appreciated :D

---

### Post by wilee-nilee on 2010-11-25
> **coomdoom said:**
> I was able to make a recovery CD from my laptop which has Windows 7. I followed the instructions for the recovery CD and they worked perfectly. Thank you very much, all your help is greatly appreciated :D

Great also check out drs305's signature, there is a whole lotta grub help going on there if you ever dual boot. And just for general understanding and use.

drs305, you really have a good eye, I was responding to the original poster, but with this users script, I guess I need some more coffee eh.;)

---

### Post by yousifmagdi on 2010-11-26
I was unable to recover my windows xp because i got asked about the administrator password while recovery, I couldn't remember it. So I just Reinstalled windows XP anyway. Now everything is back to normal. Thanks guys for Help :) I will try to read more about GRUB, sounds interesting.

---

