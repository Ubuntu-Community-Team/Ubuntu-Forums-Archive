---
title: "Repurcussions of a grub problem - How to fix?"
date: 2009-12-21
forum: General Help
---

### Post by searchfgold6789 on 2009-12-21
Hi,
maybe some of you have seen my most recent thread about an Error 22 problem in grub, which got solved. At the end of the thread my last post was about trying to install DOS. Here is my problem now.
First let me give you a view of my partition layout: I had a 120GB drive entirely dedicated to Windows XP, except for 7.41 megabytes beforehand, which was a FAT partition. Plus a 30GB for Ubuntu 9.10, which was upgraded from 9.04.
I intended to install DOS onto the 7MB FAT partition and maybe have it be read by grub. I booted from a boot diskette made by bootdisk.com, made a primary DOS partition on the 120GB drive, rebooted to the diskette, getting and A:> prompt, and {gulp} typed in:
```
sys
```Installing DOS.
Then, whenever I tried to go to "Windows XP Home Edition" from the grub menu when my computer booted, I got an A:> prompt instead of Windows. Ubuntu booted normally.
From within Ubuntu, I deleted the 7.4 MB partition and now whenever I tried to access Windows from grub I got an
```
Error 22:


No such partition
```and I do believe that my menu.lst was fine, except that it now defined HD(1,0) as the DOS partition, it being the 0th one on the disk.
But I didn't think of this then, so I panicked and booted from my XP cd and did a recovery console. I typed fixboot and, unfortunately, put windows boot files and settings onto the ubuntu disk, which it read as E: . 

:guitar:

After realizing my mistake I went ahead and fixed the windows boot hard drive's boot stuff instead, just for good measure. Oh yes and I also did a fixmbr for both disks too. :twisted::twisted::twisted::twisted: 
Now whenever my computer boots it goes into the Intel Boot agent v2.2, like it always does, and says that NTLDR is missing, whatever my BiOS settings are.
How do I repair my mbr's so that grub will appear and will let me get into windows and/or ubuntu? Thanks so much, I love this website,
Richie

---

### Post by drs305 on 2009-12-21
Here is a link on restoring Grub:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by searchfgold6789 on 2009-12-21
> **drs305 said:**
> Here is a link on restoring Grub:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
okay, but what about the poor boot sector of ubuntu? will it take care of that?

---

### Post by drs305 on 2009-12-21
> **searchfgold6789 said:**
> okay, but what about the poor boot sector of ubuntu? will it take care of that?

Yes it should. From the help page:
> 
grub-install copies GRUB images into the DIR/boot directory specified by --root-directory, and uses grub-setup to install grub into the boot sector.



---

### Post by searchfgold6789 on 2009-12-21
okay, here goes.

---

### Post by searchfgold6789 on 2009-12-21
funny...I had that site saved under my bookmarks...lol?

---

### Post by searchfgold6789 on 2009-12-21
Grub is fixed, windows and ubuntu are not.
When  try to access Windows from the grub menu, it still says
```
Error 22


No such partition
```
And when I try to access ubuntu, it begins booting and the black-and-whit ubuntu logo appears in the enter of the screen and fades, but instead of booting, a message appears saying:
```
Gave up waiting for root device. Common problems:032a8fc5683
       - Boot args (cat /proc/cmdline
           - Check rootdelay= (did the system wait long enough?)
           - Check root= (did the system wait for the right device?)
       - Missing modules (cat /proc/modules; is /dev)



ALERT! /dev/disk/by-uuid/98113y03-bf95-45fd-bae5-c032a8fc5683 does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu1:1.13.3-1ubuntu7 built-install (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```
(when you type in help it gives a list of , supposedly, built-in commands.)
'reboot' reboots and the same thing happens.
anyone know how to solve this problem?

---

### Post by stlsaint on 2009-12-21
id hate to say it but it looks as if your / was wiped...of course this is just based off what i could get from the error.

---

### Post by drs305 on 2009-12-21
One of the problems with getting to Ubuntu appears to be an invalid UUID:
> ALERT! /dev/disk/by-uuid/98113y03-bf95-45fd-bae5-c032a8fc5683 does not exist. Dropping to a shell!


You can investigate this via the LiveCD. Mount your real Ubuntu partition (sudo mkdir /mnt/test && sudo mount /dev/sdXY /mnt/test) and take a look at your /etc/fstab file. Since Grub starts to boot, the UUID error is most likely contained in one of the fstab listings.

You can get the UUIDs by running "sudo blkid".

---

### Post by searchfgold6789 on 2009-12-21
The contents of the fstab file are:
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```
when i type in sudo blkid i get
```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="98113b03-bf95-45fd-bae5-c032a8fc5683" TYPE="ext3" 
/dev/sda5: UUID="724532ba-aa91-402f-afc3-a50c45ccd9f1" TYPE="swap" 
/dev/sdb2: UUID="01CA4935A4825660" LABEL="XP Home" TYPE="ntfs" 
```

---

### Post by searchfgold6789 on 2009-12-21
ummm...was i supposed to do something?

---

### Post by drs305 on 2009-12-21
Is this your sda1 fstab file or the LiveCD fstab? To view your real system fstab file, you must mount /dev/sda1 and then open fstab with:
```
gksu gedit /mountpoint/etc/fstab
```
If you open it with "gksu gedit /etc/fstab" you will see the LiveCD fstab.

Assuming the files are there, you need to add the / partition to fstab, which appears to be ext3. Comment out the "aufs" line and add the following :

> 
98113b03-bf95-45fd-bae5-c032a8fc5683  / ext3 errors=remount-ro 	0 1


After you save fstab, reboot.

---

### Post by searchfgold6789 on 2009-12-21
well i tried to save it buuut it said i do not have permision to. from live cd.

---

### Post by searchfgold6789 on 2009-12-21
plus t comment out is it a `#' or is it a `%'  ?

---

### Post by drs305 on 2009-12-21
Mount sda1:
```

sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
gksudo gedit /mnt/sda1/etc/fstab

```
Commenting is done with the # symbol. However, you will probably see a different fstab when you open the *real* sda1 fstab.

If you open if with "gksudo" you have admin rights and it should save normally.

---

### Post by searchfgold6789 on 2009-12-21
okay, this opened a different fstab file, which is posted here:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=98113b03-bf95-45fd-bae5-c032a8fc5683 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=724532ba-aa91-402f-afc3-a50c45ccd9f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
any different instructions now?

---

### Post by drs305 on 2009-12-21
The UUIDs appear to be correct. As long as you have it mounted, you can add the Windows partition to fstab:

> 
UUID=01CA4935A4825660 /mountpoint ntfs auto,users,uid=1000,gid=100,utf8,umask=022 0 0

Save fstab, then create the mountpoint:
```

sudo mkdir /mountpoint

```

For instance, if you want to mount Windows on /media/windows, run "sudo mkdir /media/windows" and also make the /mountpoint in fstab "/media/windows" as well.

Next, it's time to look at your menu.lst, since it appears you are using Grub legacy:
```

gksudo gedit /boot/grub/menu.lst

```

I'm off now but someone else can answer your questions.

---

### Post by searchfgold6789 on 2009-12-22
tried editing the menu.lst file. Here goes the reboot..... wish me luck!

---

### Post by searchfgold6789 on 2009-12-22
I checked the menu.lst file, tweaked something at the bottom, and now there is no more Eror 22, BUT Windows complains:
Windows could not start because of a disk hardware configuration problem.
```
Could not read from the selected boot disk. Check boot path and disk hardware.
Please check the Windows documentation about hardware disk configuration and your hardware reference manuals for additional information. 
MWAHAHAHAHA!!!!! Ahem.
```So I will do some things within the recovery console to try and fix this. If you know how to fix based on my first post though, please stop me and explain. :)
Ubuntu has the same problem as before.

---

### Post by searchfgold6789 on 2009-12-22
fixboot didn't work...should i try fixmbr?
yes i should. here goes a fixmbr c

---

### Post by searchfgold6789 on 2009-12-22
...whiiiiich didn't do anything. a little help here?

---

### Post by searchfgold6789 on 2009-12-22
anybody?

---

### Post by oldfred on 2009-12-22
These are all commands, but once you fixmbr your will have to reinstall grub, if your windows boots ok.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

I think your sys command in your initial post overwrote the xp install not your new partition?

---

### Post by Leppie on 2009-12-23
> **oldfred said:**
> I think your sys command in your initial post overwrote the xp install not your new partition?

I think oldfred is right. It's been a long time since I used dos, but I believe that issuing the sys command **without** indicating the destination "drive" (i.e. partition) just installs it to c: (which would've been your xp partition).

try following the instructions to reconstruct your xp boot loader.

---

### Post by llawwehttam on 2009-12-23
in ubuntu you could try sudo grub-update .

Personally I'd use a different bootloader with a gui. Something like GAG.

gag.sourceforge.net

---

### Post by Leppie on 2009-12-23
> **llawwehttam said:**
> in ubuntu you could try sudo grub-update .
grub-update (or better **update-grub**) wouldn't work as the xp bootloader apparently is broken.

> **llawwehttam said:**
> Personally I'd use a different bootloader with a gui. Something like GAG.
what is the advantage of a gui? waiting for the bootloader to load in order to be able to boot?

---

### Post by jwbrase on 2009-12-23
Here's the deal. That 7 MB partition that you deleted was part of the Windows boot process. It contains files like NTLDR. SYS overwrote it with DOS. The Windows install itself wouldn't be touched because it's on an NTFS partition, which DOS can't read. That's why it booted into DOS instead of Windows: because the Windows boot files had been replaced by DOS. Then when you deleted it, GRUB couldn't find it so it threw Error 22. When you tried editing menu.txt to point GRUB to the main Windows partition, Windows couldn't boot from that partition, since it needs the one you deleted.

Then, as you mentioned, you borked your Ubuntu install trying to fix Windows, and I'm not exactly sure what all happened there.

You'll need to replace the partition you deleted and somehow get the necessary Windows boot files back onto it. How exactly you need to do that is over my head.

Moral: Do not SYS or format a partition unless you know what is on it, what it does, and that you don't need anything on it anymore.

If SYSing or formatting a partition, or doing anything else like that to it, results in problems, that means there was something critical on it, and you borked that something critical by doing that. ***_*NEVER*_*** (!!!) delete such a partition, unless you know what you borked, why what you did borked it, and that you don't need anything that needs it anymore (In this case, unless you don't need Windows anymore). If doing something to the partition borked something, then deleting the partition will cause *extreme* borkage.

---

### Post by searchfgold6789 on 2009-12-28
Allright, I'm still here.

jwbrase is exactly right about the process i used to mess up windows.
BUT WAIT! look at this...on my hard disk I have a file calles MSDOS.SYS!!!!!!!! will deleting that do anything???? I stil have my boot.ini...ntldr....and ntdetect.com files. The MSDOS.SYS file, of course, shows up as blank because of the sys file type. 
Look at this! I also have IO.SYS, AUTOEXEC.bat, *ANNNNNNDDD* a log file:
bootex.log
```
Checking file system on \DosDevices\C: 
The type of the file system is NTFS. 
Volume label is XP Home. 
 
The object id index entry in file 0x19 points to file 0x288c 
but the file has no object id in it. 
Deleting an index entry from index $O of file 25. 
The object id index entry in file 0x19 points to file 0x6031 
but the file has no object id in it. 
Deleting an index entry from index $O of file 25. 
Cleaning up 16 unused index entries from index $SII of file 0x9. 
Cleaning up 16 unused index entries from index $SDH of file 0x9. 
Cleaning up 16 unused security descriptors. 
CHKDSK is verifying Usn Journal... 
Usn Journal verification completed. 
Windows has made corrections to the file system. 
 
 120037679 KB total disk space. 
  13737064 KB in 53003 files. 
     18120 KB in 5957 indexes. 
         0 KB in bad sectors. 
    166719 KB in use by the system. 
     65536 KB occupied by the log file. 
 106115776 KB available on disk. 
 
      4096 bytes in each allocation unit. 
  30009419 total allocation units on disk. 
  26528944 allocation units available on disk. 
 
Internal Info: 
70 e8 00 00 5c e6 00 00 b4 4a 01 00 00 00 00 00  p...\....J...... 
dd 01 00 00 02 00 00 00 15 02 00 00 00 00 00 00  ................ 
90 4a 45 05 00 00 00 00 10 66 de 1f 00 00 00 00  .JE......f...... 
20 35 7c 07 00 00 00 00 00 00 00 00 00 00 00 00   5|............. 
00 00 00 00 00 00 00 00 b0 a2 0d 33 00 00 00 00  ...........3.... 
99 9e 36 00 00 00 00 00 18 3a 07 00 0b cf 00 00  ..6......:...... 
00 00 00 00 00 a0 71 46 03 00 00 00 45 17 00 00  ......qF....E...
```maybe i should delete some of these old-fashioned files and then fixboot! enlighten me.
The current contents of the boot.ini:
```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
```

---

### Post by searchfgold6789 on 2009-12-28
I'll start a new thread; this one's a bit old.
never mind, there's no need to aparently! the help forum is sorted by most-recently-replied-to! neat...

---

### Post by searchfgold6789 on 2009-12-28
allright, I'll replace the partition and try putting the boot files on it, which I am skeptical about, but OK.
Before I do it I need to fix the Ubuntu problem though because I can't create a FAT partition from the livecd...I'll be on...

---

### Post by searchfgold6789 on 2009-12-29
HEH heh fixed myself I changed the partition2 bits of the boot.ini file to "partition1" and it boots normally. I celebrated by copying the contents of my c:\windows\resources file to a thumb drive and getting a blue screen of death, lol.

Now I just need to fix linux.

---

