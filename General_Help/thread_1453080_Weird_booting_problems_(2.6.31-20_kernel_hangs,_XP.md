---
title: "Weird booting problems (2.6.31-20 kernel hangs, XP just reboots)"
date: 2010-04-12
forum: General Help
---

### Post by Objekt on 2010-04-12
Recently I reinstalled GRUB2 as my bootloader.  Some weird stuff is happening:

-If I boot Ubuntu with the 2.6.31-20-generic kernel, the system hangs.  I see the "pulsating Ubuntu logo" briefly, then a whole bunch of text, and the login screen briefly.  Then the screen goes blank and nothing more happens.

-If I choose to boot the 2.6.31-19 kernel, it works fine.

(I was able to boot 2.6.31-20 while I used legacy GRUB.)

-If I choose "Vista loader" (not sure of the exact text, but that's the gist), indeed the Windows bootloader screen appears.  However, only the Windows 7 option works.  If I choose "Earlier version of Windows" (which really means Windows XP), the system reboots.

FWIW, I have the Vista/7 bootloader in the MBR of one HDD, with GRUB2 in the MBR of another.  Everything above happens when the GRUB2 disk is selected as first in BIOS.  If I select the HDD with Windows 7 on it, the Vista bootloader appears & works as you would expect.  That is, I can boot XP.

Possible confounding factor: Windows 7 is on one disk (sdb below) while Windows XP is on another (sda below).  The Vista/7 bootloader is installed on disk sda.  

Probably not important, but who knows: My Ubuntu 9.10 install is on disk sdc, with the system (/) and /home on separate partitions.  There is also another ext3 partition on that disk, used for general storage.

On sdb, along with Windows 7, is an install of Ubuntu 8.04.4 LTS that I don't use very much.  When I was using legacy GRUB, the boot files, menu.lst etc. were stored in the 8.04.4 LTS system partition on sdb.

I never had a problem with this configuration when I was using legacy GRUB.  I don't know why stuff is broken now that I've replaced legacy GRUB with GRUB2.

Here's the output of fdisk -l:
```
objekt910@objekt910-desktop:~$ sudo fdisk -l
[sudo] password for objekt910: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2a6f2a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551      121601   956277157+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b2e90b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6375    51200000    7  HPFS/NTFS
/dev/sdb2            6375       62144   447970656    7  HPFS/NTFS
/dev/sdb3           62145       77827   125973697+   5  Extended
/dev/sdb5           62145       63968    14651248+  83  Linux
/dev/sdb6           63969       64454     3903763+  82  Linux swap / Solaris
/dev/sdb7           64455       69317    39062016   83  Linux

Disk /dev/sdc: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc9eeb12

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1874    15052873+  83  Linux
/dev/sdc2            1875        8880    56275695    5  Extended
/dev/sdc3            8881       20023    89506147+  83  Linux
/dev/sdc5            1875        2360     3903763+  82  Linux swap / Solaris
/dev/sdc6            2361        8880    52371868+  83  Linux

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59ecdd5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x849cac27

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001    7  HPFS/NTFS

```

So, for now, I'm stuck changing the disk boot order in BIOS if I want to boot Windows XP.  I can't use Ubuntu with the 2.6.31-20 kernel any more because it just hangs.  How do I fix this?

---

### Post by Objekt on 2010-04-13
In diagnosing the problem, I thought it might help to post the (partial) results of the well-known Boot Info Script (I have version 048, judging by the title of the script: boot_info_script048.sh).

Here's the first section of the RESULTS.TXT file, up until the section marked "Drive/Partition Info":

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Grub 1.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sde
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /grub.cfg /boot.ini
```

A little narrative that might help:

-All drives are SATA of various sizes.  One (sde) is an external HDD connected via eSATA.

-The last two drives (sdd and sde) shouldn't be part of the problem.  They are simply NTFS volumes occupying the whole disk, 320 GB and 1 TB respectively.  The Linux boot files found on the external drive (sde) are merely some files that I copied to the disk while I was trying to figure out some earlier boot-related problems.

I'll attach the entire RESULTS.TXT file.  At 27 kB, it is a bit too large to be posted directly, so I had to compress it.

---

### Post by mockingbird on 2010-04-13
The correct way to dual boot Windows and Linux:

If you're dual-booting XP and Linux there is no problem.  You can easily integrate the Linux boot into the XP boot menu.  We all know the command: "dd if=/dev/hdaX/ of=boot.bin count=512 bs=1" and then we would just edit XP's boot INI and add the entry for that boot.bin file which will take you to GRUB.

Now of course you can use GRUB to boot XP in this situation **but not with Longhorn / Windows 7.**  Even Grub2 cannot boot Longhorn properly (At least with my Debian Lenny install).

The only thing I have gotten to work with Vista is the following.  You will need to play with Vista / 7's BCD entries.  BCD is the new system it uses.  Vista or 7 will have to be the main OS (That is, the one on the partition set to bootable) and then you can add the boot.bin entry by using bcdmgr or bcdedit (I forget the command) like you did in XP.

For some reason, I had some problems booting to GRUB with 10.04 Lucid Beta 1 after doing the updates, but now with Beta 2 this problem seems to have been fixed.

---

### Post by Objekt on 2010-04-13
Your problems with GRUB and Vista/7 must be peculiar to Debian Lenny, or perhaps your hardware.  I've never had a problem getting GRUB to kick off the Vista/7 bootloader, either legacy GRUB or GRUB2, on a variety of machines.  I never had to mess with dd commands.  I never considered trying to get the Vista/7 bootloader to recognize & boot Ubuntu, because using GRUB/GRUB2 as my bootloader was so much easier.

The problem I'm having is this: the Vista/7 bootloader acts differentlly, depending on whether it's loaded first, or called through GRUB2.  

That makes no sense at all, because things didn't work that way when I first used GRUB2, a few months ago.

---

### Post by Objekt on 2010-04-15
Anyone?

---

### Post by Objekt on 2010-04-16
[s]FWIW, I'm no longer having the 2.6.31-20 kernel hang.  But the other boot problem is still there.[/s]

Scratch that, still having issues occasionally.  Yesterday I couldn't boot with the 2.6.31-19 kernel either.

I seem to have a disk partition that's refusing to mount sometimes, for non-obvious reasons.  Probably less confusing if I start a new thread about that.

---

### Post by Objekt on 2010-04-20
Sorta-solved.  See other thread here: [http://ubuntuforums.org/showthread.php?p=9149280#post9149280]("http://ubuntuforums.org/showthread.php?p=9149280#post9149280")

Nutshell: Not mounting the swap partition solved the boot hang problem, but that's not a real solution, only a temporary fix.

Still having the XP booting problem.

Instead of trying to use the Windows 7 bootloader to start XP, I guess I'll have to reinstall the XP bootloader on the MBR of the disk XP is on.  Then I can have GRUB2 go directly to the XP bootloader, instead of the Win 7 one.

---

### Post by oldfred on 2010-04-20
Yes you may have to repair the XP boot loader. Windows combines all windows boot into the active partition (boot flag). It moves some of the second windows install files into that first partition and grub or other boot loaders cannot directly boot it.

Lots of detail on multibooters site, if not interested in all the detail at least review the pictures to understand some of the windows boot process.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by Objekt on 2010-04-21
Here's the latest weirdness.

Last night, I restored the Windows XP bootloader to the first HDD by running the Windows XP install CD and going into Recovery Console, fixmbr, fixboot, done.  Right?  The system now boots XP without issue, as long as I make that hard drive first in BIOS.

I then changed the setting in BIOS so that my HDD with GRUB2 on it would be first.  I booted Ubuntu and ran "update-grub," thinking it would detect the XP bootloader on the appropriate hard drive.  No such luck.  It said the "Windows 7" bootloader was on that drive.

If I select the "Windows 7" option on the GRUB menu at boot time, XP still does not boot.  Instead there's a lot of beeping from my computer, a blank screen, and then I have to manually reboot it.

What the heck is going on here?!

---

### Post by oldfred on 2010-04-21
It looks like your windows 7 was booting thru the XP boot. Before when you booted it was loading from the active (boot or *) partition and then gave you a choice of which to boot. The /Boot/BCD that was/is in your XP partition was from win7. You may then be able to repair the win7?

---

### Post by Objekt on 2010-04-21
Yes, I was able to get the Windows 7 bootloader installed previously, and I would have no trouble doing it again.  The Win 7 setup DVD-ROM makes it quite easy.  

The problem is that it does not help.  I can start XP using either the Win 7 bootloader or the XP bootloader by itself, but I cannot start XP through GRUB2, at all.

I am in pretty much the same situation now that I was when I started the thread.  I still have to manually switch which HDD is "first" in BIOS to boot Windows XP instead of Ubuntu.  It's very annoying and wastes more time than usual, because I have to reboot twice: once to access the BIOS menu, then again to start the chosen OS.

How does GRUB2 still think I have the Windows 7 bootloader installed?  It is no longer on any of my hard drives, as far as I know.

---

### Post by oldfred on 2010-04-21
I am not sure exactly what grub looks at but because the boots were combined the XP will look like win7. If you look at the boot info script it shows the partition as win7, so it also saw it as 7.

If you unplug each drive and then repair it so one windows does not see & combine the other?? You have to have a boot flag(active partition) on each version.

---

### Post by Objekt on 2010-04-21
The bootinfo script results I posted previously are obsolete, actually.  I haven't re-run the script since I reinstalled the XP bootloader on the hard drive where XP lives.  Previously, that disk had the Windows 7 bootloader in the MBR.

It seems likely there is something left on the XP hard drive that makes GRUB2 think that the Win 7 bootloader is still present there.  I guess that disk is "tainted" so to speak. 

I think the next thing I will try is reinstalling the Windows 7 bootloader to the second 1 TB drive, which is where Windows 7 is physically present.  The Win 7 bootloader seems pretty "smart," and will probably notice the XP install on the other disk & let me try to boot it.

---

### Post by Objekt on 2010-04-23
I decided to simply start over, with a second Windows XP install.

It boots properly when called by GRUB2.  I still have no idea why XP freaks out when I use GRUB2 to kick off the Win 7 bootloader, and then my old XP install.

By reinstalling XP, I got rid of one problem I had with the old XP install: it incorporated the ICH9R RAID driver, which both requires the ICH9R to be in RAID mode, regardless of whether you are actually using disks in RAID configuration.

---

