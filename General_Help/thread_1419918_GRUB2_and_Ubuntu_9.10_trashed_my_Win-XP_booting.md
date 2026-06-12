---
title: "GRUB2 and Ubuntu 9.10 trashed my Win-XP booting"
date: 2010-03-02
forum: General Help
---

### Post by aqk on 2010-03-02
Preamble: 
 I just upgraded someone's old WinXP system with a new 200 Gig HD, and re-installed his XP on it. And then applied all the WinXP SP3 + fixes. 
As well as add a few other things - Win Defender, Avast-5-free, apps, etc..
**His Windows XP was now running GREAT!** 
And his old 80 Gig HD was retired.

Things went so well, that I decided "Why not add Ubuntu 9.10 to a spare partition on the drive?"
  So I booted from a Ubuntu 9.10 CD and added the Ubuntu into a 30 Gig Ext3 partition, and a 2 Gig swap.
  Rebooted and guess what?  When I choose WinXP from the grub menu, the PC just hangs.
 **"He's DEAD, Jim."**  -*Dr.McCoy.*
 The Ubuntu system of course works. So now the user has a Ubuntu system, but no WinXP. He is NOT HAPPY.
  According to the Ubuntu, the 20Gig Win-C boot partition is still there, including its boot.ini and ntldr files. 
  -------------------  

 Problem Details:
   The 30_OS-prober finds the Windows partition, but since then I have added a 11_Windows to the grub.d folder (yes with "x" privileges).
 The 11-Windows is as follows: 
  ==============================
#! /bin/sh -e
echo "Adding aqk's Windows XP on blkid 7C791A613AEEE09F..." >&2
cat << EOF
menuentry "Windows XP" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7C791A613AEEE09F  
chainloader +1
}
EOF 
     ===========================

  Clicking either the 11_windows or the 30-OS-prober entries in the grub boot-time menu give the same result:
  The System goes dead. And I must press the off-button to reboot.
   Of course the linux entries in the grub menu work just fine! 

  :confused:  Anyone have any ideas?
   Thanx.

---

### Post by bcbc on 2010-03-02
grub2 should automatically find XP without adding the 11_Windows entry. If you want to customize the grub menu try this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")

I'd take out your 11_ Windows file, rerun 
```
$ sudo update-grub
```
and if that doesn't work, then run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.
If it booted windows then follow the first link to customize the grub menu to how you want it.

Edit: I just reread and saw you already tried the os prober windows entry. So scratch what I said, and just post the bootinfoscript result.

---

### Post by aqk on 2010-03-02
Thanx!  Bootinfoscript, huh?
 Never heard of it before - but sounds promising!

Please bear with me- I'm limited to dialup here, and am currently DLing the rest of Karmic's  122 meg of updates here.  Response is now very slow  obviously!  ;) 
Will post the bootinfo  once I can DL it!

---

### Post by bcbc on 2010-03-02
ok, by the way, here's the entry that boots my XP. It's different from yours.
```

menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
insmod ntfs
set root=(hd0,2)
search --no-floppy --fs-uuid --set 10ace996ace9769e
drivemap -s (hd0) ${root}
chainloader +1
} 
```

Note: the "set" with UUID part should be different. Also my XP is on partition sda2 (i.e. hd0,2). You should be able to check the partition by typing in terminal:
```
$ sudo fdisk -l
```
If yours is on sda1 then you'd use hd0,1.

---

### Post by aqk on 2010-03-02
BCBC,
 here's the output of my  Boot_info-script - see below. 

  But I am guessing that you *may* detect the problem in the first few lines:  
The  **Boot sector is Vista/Win7 but the op system is XP**.
I remember now formatting all the partitions when the disk was externally mounted on my Vista laptop!   
  MEA CULPA!  
But the XP installed and booted properly many times thereafter.  Go figure! 
It was only when I installed Ubuntu 9.10 and its boot2, that the Win-XP was no longer detected.
Do you think this is the problem? Any other suggestions?
More info at [**http://support.microsoft.com/kb/919529**](**http://support.microsoft.com/kb/919529**)   

  If it is the problem, all I have to do is figure out **how to revert the MBR back to an XP format, as per the MS bulletin above....** 
presumably booting from an XP CD I have hanging around and then dropping into command mode...

 PS-  Thats's a neat li'l shell script!   Thanx!

  Boot-info-script  output:  
  -------------------------
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b36bdea

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,945,714    41,945,652   7 HPFS/NTFS
/dev/sda2         327,806,325   390,716,864    62,910,540   b W95 FAT32
/dev/sda3          41,945,715   327,806,324   285,860,610   f W95 Ext d (LBA)
/dev/sda5          41,945,778   104,856,254    62,910,477   7 HPFS/NTFS
/dev/sda6         104,856,318   230,693,399   125,837,082   7 HPFS/NTFS
/dev/sda7         323,613,423   327,806,324     4,192,902  82 Linux swap / Solaris
/dev/sda8         263,610,648   323,613,359    60,002,712  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7C791A613AEEE09F                       ntfs       C-XP-SYSTEM                   
/dev/sda2        41C2-B4B9                              vfat       AQK-SAVEDST                   
/dev/sda5        5736E6F521B288AC                       ntfs       Data-Alex                     
/dev/sda6        591C57D614745EE7                       ntfs       Music-etc                     
/dev/sda7        d85272a3-a741-4ad7-87b3-98956617d94d   swap                                     
/dev/sda8        d83836f8-98d8-4997-9cdd-835a21f658dd   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/C-XP-SYSTEM       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="2"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,8)
search --no-floppy --fs-uuid --set d83836f8-98d8-4997-9cdd-835a21f658dd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=33
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=green/black
set menu_color_highlight=yellow/red
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set d83836f8-98d8-4997-9cdd-835a21f658dd
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=d83836f8-98d8-4997-9cdd-835a21f658dd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set d83836f8-98d8-4997-9cdd-835a21f658dd
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=d83836f8-98d8-4997-9cdd-835a21f658dd ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set d83836f8-98d8-4997-9cdd-835a21f658dd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d83836f8-98d8-4997-9cdd-835a21f658dd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set d83836f8-98d8-4997-9cdd-835a21f658dd
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d83836f8-98d8-4997-9cdd-835a21f658dd ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows XP-SP3 plus Win-updates" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7C791A613AEEE09F
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 7c791a613aeee09f
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=d83836f8-98d8-4997-9cdd-835a21f658dd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=d85272a3-a741-4ad7-87b3-98956617d94d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 135.5GB: boot/grub/core.img
 135.2GB: boot/grub/grub.cfg
 135.5GB: boot/initrd.img-2.6.31-14-generic
 136.0GB: boot/initrd.img-2.6.31-19-generic
 135.5GB: boot/vmlinuz-2.6.31-14-generic
 135.7GB: boot/vmlinuz-2.6.31-19-generic
 136.0GB: initrd.img
 135.5GB: initrd.img.old
 135.7GB: vmlinuz
 135.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde    <<===  These USB drive slots seem to give errors on the Update-grub2   
   ---------------------------------------------

---

### Post by bcbc on 2010-03-02
Yes, I believe you're right. You need to repair the boot sector using the XP recovery cd. Then you'll have to boot ubuntu using the live CD and reinstall grub2 to get your dual boot back.

I'll look around for a step by step for you.

---

### Post by meierfra. on 2010-03-02
Boot from  your XP CD.  Press "r" to enter the repair console. If asked for a password  just press "enter" (unless you actually did set a password)  Then type

```
fixboot
```

> Then you'll have to boot ubuntu using the live CD and reinstall grub2 to get your dual boot back.

As long as you just run "fixboot" you won't  have to reinstall Grub.

---

### Post by bcbc on 2010-03-02
> **meierfra. said:**
> Boot from  your XP CD.  Press "r" to enter the repair console. If asked for a password  just press "enter" (unless you actually did set a password)  Then type

```
fixboot
```


As long as you just run "fixboot" you won't  have to reinstall Grub.
Cool - that's easier than I thought.

---

### Post by aqk on 2010-03-02
Thanx, guys...  will try the fixboot option.  Tomorrow. 
Alas, my old DELL XP install disk (with a counterfeit win license key) will not let me access the "real" C: drive or the MBR, (why?  I don't know) and the "official" E-machines XP-Home install disks I have - FOUR CDs! - tell me that I have SP3 installed and refuse to go any further, unless I agree to  re-formatting the whole mess.  Grrrr...! 

  I went back to a very old W2K CD I had, but alas it was not bootable.
Will try tomorrow to DL some boot utility that has Fixboot on it or that I can copy fixboot onto... 

Too tired and [***plonqued out***]("http://www.plonque.com") tonight to go any further..:popcorn:     A demain... 
  -aqk

---

### Post by meierfra. on 2010-03-04
If you haven't found a Recovery CD yet:

[http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip](http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip)

If that does not work, let me know.  I can give you a file with an XP boot sector to download,  and you can use "dd" to copy it to your boot sector.

---

### Post by aqk on 2010-03-06
Thanx for the webtree link.
OK, I DLed the Webtree zip, burnt the CD, ran it and guess what?
There is NO fixboot.exe on it. 

But I saw a "bootfix.bin" command on it.
When I ran it,  it gave me the usual "Ya really wanna do this?" message,
and since I had nothing to lose, I replied "y".

[B]Guess what?  I DID have something to lose:  My Ubuntu partition!
Now I have nothing -  just a "NTLDR not found - press any key to reboot"   LOL.[/B]

I'm goin' from bad to worse.
Anyhow I have a paid-for utility "Active Partition Recovery"  from [www.lsoft.net](www.lsoft.net).  It is currently performing an extended disk scan, and hopefully after an hour or two, will allow me to rewrite the MBR with the partitions that it found.
 Sadly, I suspect it may not find the EXT4 partition....

**WHAT IS IT WITH THIS MYSTERIOUS  FIXBOOT.EXE** ???
Does it really exist?  Or is it just some MS madman's idea of torture?

---

### Post by aqk on 2010-03-10
AGAIN! 
** Ubuntu 9.10  screwed up my XP system!** 
After recovering my XP system using proprietary software from LSOFT.NET, and using it (including several planned re-boots!) for a few days, I decided to install Ubuntu 9.10 on the disk.
  But this time I was ready!  I had found an XP basic boot disk with FIXBOOT and FIXMBR on it.

I installed Ubuntu 9.10  in its own partition, rebooted, got the grub2 menu and chose the Windows XP option.

  Nothing happened.  Windows XP was DEAD. All I could do was press the On-Off button.
**Of course Ubuntu booted OK!** 

So I got my Windows XP boot recovery disk out, booted from it, and ran fixboot c:

  Guess what?  
After rebooting, I got the **"NTLDR NOT FOUND"**
**Thank you, Fixboot! **
 If Ubuntu can trash my Windows, well, Fixboot and Fixmbr can trash the whole MBR! 

Luckily I have a backup of the MBR, saved by running "Active partition Recovery" from [www.lsoft.net](www.lsoft.net) 
This software however, does not recognize EXT3 or 4 partitions, just Windows formats. But perhaps that's just as well.

IT IS A REAL DRAG TO extract the Hard-Drive from this PC, and run it as an external disk on another windows machine in order to repair the MBR problem.

  **UBUNTU 9.10  has now OFFICIALLY BEEN BANNED FROM THAT MACHINE!** 

And please don't tell me about supergrub and other grub utilities- I have tried 'em all!

---

### Post by bcbc on 2010-03-10
> **aqk said:**
> AGAIN! 
** Ubuntu 9.10  screwed up my XP system!** 
After recovering my XP system using proprietary software from LSOFT.NET, and using it (including several planned re-boots!) for a few days, I decided to install Ubuntu 9.10 on the disk.
  But this time I was ready!  I had found an XP basic boot disk with FIXBOOT and FIXMBR on it.

I installed Ubuntu 9.10  in its own partition, rebooted, got the grub2 menu and chose the Windows XP option.

  Nothing happened.  Windows XP was DEAD. All I could do was press the On-Off button.
**Of course Ubuntu booted OK!** 

So I got my Windows XP boot recovery disk out, booted from it, and ran fixboot c:

  Guess what?  
After rebooting, I got the **"NTLDR NOT FOUND"**
**Thank you, Fixboot! **
 If Ubuntu can trash my Windows, well, Fixboot and Fixmbr can trash the whole MBR! 

Luckily I have a backup of the MBR, saved by running "Active partition Recovery" from [www.lsoft.net](www.lsoft.net) 
This software however, does not recognize EXT3 or 4 partitions, just Windows formats. But perhaps that's just as well.

IT IS A REAL DRAG TO extract the Hard-Drive from this PC, and run it as an external disk on another windows machine in order to repair the MBR problem.

  **UBUNTU 9.10  has now OFFICIALLY BEEN BANNED FROM THAT MACHINE!** 

And please don't tell me about supergrub and other grub utilities- I have tried 'em all!

It's hard to say what might be going on - not knowing exactly what you're doing. I don't understand how installing ubuntu to a separate partition would interfere with your XP partition - all it does is install Grub2 to the disk master boot record (it doesn't interfere with the files on the partition containing the windows operating system). 

Here's a link someone posted recently that explains this in more detail: [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Edit: Not that I think it will necessarily solve your issue, but I found it interesting.

---

### Post by aqk on 2010-03-11
> **bcbc said:**
>  I don't understand how installing ubuntu to a separate partition would interfere with your XP partition - all it does is install Grub2 to the disk master boot record (it doesn't interfere with the files on the partition containing the windows operating system). .
  
Thanx for the pointer to [www.multibooters.co.uk](www.multibooters.co.uk) ! 
AS I said, Grub2 and Ubuntu don't interfere with the XP files or partitions; they just seem to screw up the boot sectors.
It MAY have something to do with the disk having originally been formatted by Vista. 
  
  In any event, I will recover my XP NTFS partitions - a 15-20 minute HARDWARE job, unbolting hard disk, etc - and a 2-minute software job (restoring my backed-up partition info saved on my Win7 system, using Lsoft's Act-Part-recovery) 
  
  Once the XP system is up and running again, I'll give GAG4 a try as suggested in the link you gave me.
And AGAIN will re-install UBU-910. 

(it's too bad the [**www.lsoft.net**](**www.lsoft.net**) software above does not bother with EXTn  partitions- I'll suggest it to them!)

  If Ubuntu and Grub2 again screw up my bootsectors, well,
THIS time I will definitely never try Ubuntu on this system again!  ;-) 
 There's only so much I can play with. My "serious" work is getting into a backlog! 
Again, thanx for the link to [www.multibooters.co.uk](www.multibooters.co.uk)

---

### Post by bcbc on 2010-03-11
> **aqk said:**
> 
  If Ubuntu and Grub2 again screw up my bootsectors, well,
THIS time I will definitely never try Ubuntu on this system again!  ;-) 
 There's only so much I can play with. My "serious" work is getting into a backlog! 
Again, thanx for the link to [www.multibooters.co.uk](www.multibooters.co.uk)

You're welcome. 

Another idea is not to install grub2 to the MBR but get Windows to boot ubuntu (I don't mean wubi). I haven't done this before but I've read a howto somewhere. [http://oreilly.com/linux/archive/dual-boot-laptop.html?page=3](http://oreilly.com/linux/archive/dual-boot-laptop.html?page=3) (*note grub numbering has changed (hd0,1) is partition 1 now, used to be partition 2 as described in link)

Good luck.

---

