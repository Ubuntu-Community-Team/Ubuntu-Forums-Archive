---
title: "Grub2 stopped booting windows - can't get it fixed"
date: 2010-05-20
forum: General Help
---

### Post by krbuck on 2010-05-20
I'm dual-booting Ubuntu 10.4 (grub2) and Windows 7 (x64). Something stomped on my grub install on the windows boot sector (probably windows). I was getting errors like "Cannot find disk.." I updated my grub.cfg to what I thought should work and now I'm getting errors like "cannot find C/H/S values".

I've attached the RESULTS.txt. Its really a simple install, although I do have a RAID5 array; the RAID disks are just for data and hold no OS files. Both OS's are on /dev/sdd.

Probably a simple problem; I'm grateful for any help.

---

### Post by krbuck on 2010-05-21
bumpers.

---

### Post by philinux on 2010-05-21
First off I would run this in ubuntu.

```
sudo update-grub
```
Then try rebooting and booting into windows.

If that does not work then I would reinstall grub from the livecd.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by krbuck on 2010-05-21
> **philinux said:**
> First off I would run this in ubuntu.

```
sudo update-grub
```Then try rebooting and booting into windows.

If that does not work then I would reinstall grub from the livecd.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)


Thanks philinux, I did try this, as one of the things to recover, but it just removed windows from the grub.cfg.

I guess I'll have to go to the livecd unless someone else has another idea.

Thanks.

---

### Post by bumanie on 2010-05-21
Go [to here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") and see if this may help. 10.04 has had this problem re dual booting and those instructions, generally fix it.

---

### Post by krbuck on 2010-05-21
> **bumanie said:**
> Go [to here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") and see if this may help. 10.04 has had this problem re dual booting and those instructions, generally fix it.

I did try this earlier with no result. It is still giving an error about not finding "C/H/S", which I assume is cylinders, heads, sectors or such.

This is very strange; perhaps particular to my hardware setup. I did have this working at one time.....

---

### Post by oldfred on 2010-05-21
You do have the problem where you installed grub to every partition. I do not what what grub then does to a raid setup, I hope you did not also select all the raid partitions.

Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

But your sdd1 does not have the full windows. The script is not able to parse the raid set, but your sda1 looks like it is/was the 100MB windows boot partition and your sdd1 only has 
/boot.ini /Windows/System32/winload.exe
The boot.ini is a XP file so I do not know why it is there??

But you are missing the files normally in a windows 100MB boot partition. /bootmgr /Boot/BCD 
If testdisk will not repair this partition and remove the grub in the boot sector then you will  have to run windows repairs. You also have to put a boot flag on sdd1 or windows will not see it. You can use gparted to add boot flag. Right click on partition and manage flags.

sdd1: ____________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sdd1 and 
                       looks at sector 1239107354 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.[/COLOR]
    Operating System:  Windows 7
    Boot files/dirs:   [COLOR=DarkRed]/boot.ini[/COLOR] /Windows/System32/winload.exe

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by krbuck on 2010-05-21
I'm not sure where the boot.ini came from. This is a new system and the only xp that has been on the disk is from VMWare.

Thanks for the tips; I ran the bootrec commands minus the mbr restore which would have nuked grub. the fixboot and rebuildbcd options both had errors "**Element not found"**.  I will dig further using the links provided but...

Is it just easier at this point to use windows to manage multiboot? Any other ideas?

Thanks again.

> **oldfred said:**
> You do have the problem where you installed grub to every partition. I do not what what grub then does to a raid setup, I hope you did not also select all the raid partitions.

Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

But your sdd1 does not have the full windows. The script is not able to parse the raid set, but your sda1 looks like it is/was the 100MB windows boot partition and your sdd1 only has 
/boot.ini /Windows/System32/winload.exe
The boot.ini is a XP file so I do not know why it is there??

But you are missing the files normally in a windows 100MB boot partition. /bootmgr /Boot/BCD 
If testdisk will not repair this partition and remove the grub in the boot sector then you will  have to run windows repairs. You also have to put a boot flag on sdd1 or windows will not see it. You can use gparted to add boot flag. Right click on partition and manage flags.

sdd1: ____________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sdd1 and 
                       looks at sector 1239107354 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.[/COLOR]
    Operating System:  Windows 7
    Boot files/dirs:   [COLOR=DarkRed]/boot.ini[/COLOR] /Windows/System32/winload.exe

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by krbuck on 2010-05-21
In desperation, I even tried the bootrec /fixmbr which completed without errors, but now the system doesn't even boot to the hard drive at all. I'm going backwards instead of forwards.

Sheesh. Any other ideas?

---

### Post by oldfred on 2010-05-21
Which drive did windows then install its boot loader to and is that the one you use for booting. Check BIOS and the boot script will tell you which drive has the windows boot loader.

---

### Post by krbuck on 2010-05-21
Ok, I think I see what happened here. Windows automatically created a partition in my raid 5 array (/dev/sda) and put the boot files and manager there. I missed this during install.

What's best here? I put all my OS partitions on sdd since I had trouble building the array I wanted on the other controllers. Should I try making a new partition on sdd and copying the windows boot files over there and reinstall grub from the livecd?

I remember having trouble building the raid array on sdd which is what I'd really like to do and put the OS on sda. sigh. what a mess.

---

### Post by oldfred on 2010-05-21
Does your windows boot if you boot sda?

You can just install grub2 to sdd and leave everything as it is. I do not know if you can move the windows boot partition without problems.

---

### Post by krbuck on 2010-05-21
I created /dev/sdd4 as an ntfs partition and copied over the boot files there. I tried rerunning the bootrec files with the same missing element problem. 

At least grub finds Windows 7 loader now in both places, but it doesn't boot - it just hangs there with a black screen and blinking cursor. I think I'm close to closing this one - how do I point the boot loader to /dev/sdd1?

krbuck@krbuck-desktop:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x005ca91e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      243202  1953414144    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x005ca91e

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0eae5be4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              19       77114   619273620    7  HPFS/NTFS
/dev/sdd2           77115      120325   347092357+  83  Linux
/dev/sdd3          120326      121601    10249470   82  Linux swap / Solaris
/dev/sdd4               1          18      144553+   7  HPFS/NTFS

Partition table entries are not in disk order

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdd4
Found Windows 7 (loader) on /dev/mapper/isw_ibcijadhe_Volume01
You have a memory leak (not released memory pool):
 [0x118f8a0]
You have a memory leak (not released memory pool):
 [0xd998a0]
You have a memory leak (not released memory pool):
 [0x14bbd00]
done

---

### Post by oldfred on 2010-05-21
Windows has to have a boot flag. gparted, right click manage flags, or disk utility. But I do not think grub uses the boot flag, just a windows boot loader in the MBR looks for the active (flag) partition. With the flag on sdd4 you may have to run repairs to get it to see everything correctly.

Since you have gpt you may want to download gdisk.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
The emergency disks that include GPT fdisk are:
    * SystemRescueCd
    * PartedMagic 
sudo parted /dev/sda unit s print
gdisk -l /dev/sda
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

---

### Post by lilsavalex on 2010-05-21
I had this problem once and to fix it i had to do
sudo grub-install /dev/sdb
sudo lilo -M /dev/sdb mbr

I'm not sure if this would help, but its worth a try =]

---

### Post by krbuck on 2010-05-21
oldfred,

Ok, that's pretty interesting. I set the boot flag on /dev/sdd4. I then  ran gdisk and then ran repairs using the windows boot disk (hope that  was the repairs you were referring to). 

I'm getting the same error. Any way to just move the boot loader over to /dev/sdd1?

> **oldfred said:**
> Windows has to have a boot flag. gparted, right click manage flags, or disk utility. But I do not think grub uses the boot flag, just a windows boot loader in the MBR looks for the active (flag) partition. With the flag on sdd4 you may have to run repairs to get it to see everything correctly.

Since you have gpt you may want to download gdisk.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
The emergency disks that include GPT fdisk are:
    * SystemRescueCd
    * PartedMagic 
sudo parted /dev/sda unit s print
gdisk -l /dev/sda
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

---

### Post by oldfred on 2010-05-21
I have seen several cases where the separate boot partition was not repaired. I think the only success I have seen is where the boot flag is put on the main partition and that is repaired so all booting is thru the main partition. That is the same as a win7 upgrade or install to a previously formated partition. The boot partition then is not used.

I do not know if you move /bootmgr /Boot/BCD or win repair disk will just install them?

---

### Post by krbuck on 2010-05-22
Hm, no joy. I tried moving it to /dev/sdd and now it doesn't even get to grub or boot at all; it just sits dead. I could get linux booting again with the livecd I'm sure, but I am at the point where I will just try moving my OSs to /dev/sda and just try to reconfigure my RAID. 

Need to get some sleep first; I'll check again tomorrow in case anyone has any other great ideas. If not, thanks very much to all that contributed!

---

### Post by oldfred on 2010-05-22
I missed this before and Darko caught it on another thread with gpt issues.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
I added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
I can now see all the partitions on my IDE drives and boot from them too!!!!!

---

### Post by krbuck on 2010-05-23
I gave up and punted. 

I moved all my OS partitions over to /dev/sda and recovered using their respective recovery methods.

It turns out my system just really hated booting from /dev/sdd and it all works now. I just need to rebuild my RAID disks and all should be good.

Thanks to everyone that attempted to help with this. I just mark it down to strangeness with my hardware setup.

---

