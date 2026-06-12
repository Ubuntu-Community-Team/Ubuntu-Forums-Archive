---
title: "Accidently overwrote ubuntu bootrecord with win XP, can't boot now!"
date: 2011-10-24
forum: General Help
---

### Post by Xtensity on 2011-10-24
Okay, this is an odd situation I am in.


Let me explain the partitions I have on my drive at the moment and how it got messed up.

I had my main hard disk, with Windows 7 Partition on it, and an Ubuntu Partition.

I used ubuntu primarily, I never really went on windows 7 due to a number of problems that installation had. Anyways, today i had burned myself a copy of WinXP 64x, and planned to create a separate partition for it.

I only need windows for like 3 programs for my business so I chose to go with XP instead of 7. I created an empty partition in GPARTED for about 30 gigs. I restart, with the XP disc in, and choose to install. It only sees the C:/ Drive, but it sees the entire disk...which is all my partitions. So I figured I would click that and it would begin to install. 

I can't really tell you what happen from that point, but now none of my OS's boot. They all give me windows boot loader errors(including the ubuntu installation). Windows XP did something with my ubuntu boot loader in the ubuntu file system :(.

As of right now, I am running 10.10 Maverick off a live CD I burned, trying everything to get grub to load up. 

Here are the things I have tried to fix my issue so far:
*Also, I can not burn any CDs because when I take out the 10.10 Live CD, nothing responds and I can't burn a blank CD...

The first thing I did, or tried to do, to reinstate GRUB was... from the live CD, go into grub and do:
root (hd0,0)
setup (hd0)

With this, the first command didn't even register, saying that there was no hard disc... obviously there is because I can access all the files fine through the live CD GUI. 

The next thing I tried was using the Boot-Repair program to repair the MBR and reinstall grub. 
I tried several variations of settings, and none got me anywhere.

I can't boot the ubuntu partition directly or I get the error "Missing Operating System"(a windows error). No matter what partition Boot-Repair installs grub on, "successfully", grub never loads. 

I'm at a dead end and I really need to fix this issue. I have to go back to work tomarrow and I can't work without my files and OS's! Please Help!

Also, if you have ANY idea, on how to create a partition that the windows XP installation disc can see any install to, then please say so. It has not been able to see NTFS formated partitions, NOR has it been able to see unallocated partition space. Only the C drive...Which I tried to install on and it got ****** up, and here I am now.

---

### Post by OneXero on 2011-10-24
Quick and dirty? Use an external HD/USB and back up your important files. Unless you have a bunch of applications to reinstall, it'll be the quickest. Then you can format and reinstall completely.

You could load windows recovery CD and use bootrec.exe /fixMBR and similar commands to fix the Master Boot Record. 

Alternatively, I've found that reinstalling Ubuntu can sometimes fix Boot problems and you can use the advanced partition table to make sure you don't delete anything.

---

### Post by Xtensity on 2011-10-24
I'm not going to reinstall my entire OS.... Not even the windows recovery disc could fix the master boot record. The windows boot record has never been able to start ubuntu anyways from my experience... though I'm not sure. I do not have another hardrive that I can use for backup, nor can I afford one for at least 2 weeks... 

OH. I forgot to mention, I also tried RESCATUX to fix grub, but I got an error saying grub was not installed, something went wrong :(.

I also used RESCATUX to install windows MBR to the windows partition, but that didn't seem to help much.

---

### Post by Quackers on 2011-10-24
You need to re-install grub to the mbr of the drive from a live cd/usb desktop.
Please post the output of ```
sudo fdisk -lu
```

---

### Post by martinr on 2011-10-24
> **Quackers said:**
> You need to re-install grub to the mbr of the drive from a live cd/usb desktop.
Please post the output of ```
sudo fdisk -lu
```

I agree, that is most definitely the fastest and most elegant option. Grub will also pick up on your Windoze partition.

Before installing Grub, make a backup copy of your MBR, just in case.
```

Create backup of MBR (use a live CD):
$ dd if=/dev/sda of=MBR-backup bs=512 count=1

Restore MBR with:
$ dd if=MBR-backup of=/dev/sda bs=512 count=1

```

---

### Post by Xtensity on 2011-10-24
> **Quackers said:**
> You need to re-install grub to the mbr of the drive from a live cd/usb desktop.
Please post the output of ```
sudo fdisk -lu
```

This was run from RESCATUX, and not the live CD, but the command seemed to work.

user@debian:~$ sudo fdisk -lu

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2        20996955   544458751   261730898+   7  HPFS/NTFS
/dev/sda4   *   606525440   781422591    87448576   83  Linux

---

### Post by Quackers on 2011-10-24
According to that you have just 2 partitions. 
sda2 holds Windows and sda4 holds Ubuntu. No Windows system reserved partition and no swap space for Ubuntu.
Would that be correct?

---

### Post by Xtensity on 2011-10-24
> **Quackers said:**
> According to that you have just 2 partitions. 
sda2 holds Windows and sda4 holds Ubuntu. No Windows system partition and no swap space for Ubuntu.
Would that be correct?


uhm, well before, sda1 was a recovery space, which I discovered had an unbootable, faulty version of windows vista home on it, so I deleted it. Deleting this seemed to change absolutely nothing. sda3 was an empty partition made SO i could install XP onto it, but that didn't work,so I deleted it to have that extra unpartitioned space if I needed it.

So yet, I only have these 2 partitions at the moment. 

To be precise, sda2 has Windows 7, Windows 7 Ultimate, and ubuntu on it, none of which boot if I try to load that partition(All gives boot record errors), yet it allows me to choose which operating system I want to load(Windows boot loader, on that partition), whichever one I try to load will give boot loading errors, it's really confusing, don't ask. I try to avoid that partition. All I need it for are the physical files on it.

Edit: My main focus at the moment is trying to figure out why I can not load grub, or why I can not boot the ubuntu partition without getting "Missing operating system"

---

### Post by Quackers on 2011-10-24
In a normal Ubuntu installation it is a simple matter to re-install grub.

To be sure of what commands to give you please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or alternatively, have a look here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

---

### Post by WasMeHere on 2011-10-24
It is always possible to run your computer with a live session from your boot CD with Ubuntu 10.10. If nothing else works until tomorrow, that is an option. I guess that you can mount your partitions on the hard drive and read/write your 'files for work' that way.

In general, don't do very much with your partitions without a backup, because it is risky! I think however, that you can try to reinstall or repair grub.

Did you try what is suggested in the following links?
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
[[COLOR="RoyalBlue"]_http://odzangba.wordpress.com/2011/05/14/455/_[/COLOR]]("http://odzangba.wordpress.com/2011/05/14/455/")

Good luck :-)
Olle

---

### Post by Xtensity on 2011-10-24
> **Quackers said:**
> In a normal Ubuntu installation it is a simple matter to re-install grub.

To be sure of what commands to give you please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or alternatively, have a look here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

I will get right on that as soon as I finish transfering these 60gb work files I have. I got a friend to come over and give me a removeable hard drive to barrow in the worst case. I don't want to have to resort to reinstalling everything, but if worse comes to worse, then what can you do haha. 

I'll post within 30 minutes letting you know the results.

---

### Post by Quackers on 2011-10-24
No problem.

---

### Post by OneXero on 2011-10-24
Yeah, to get a feel for these things I've tried a bunch of wacky thing and broken my computer more than a few times. Sometimes the best fix was to simply reinstall. I am no linux wizard, but sometimes the supposed solutions just don't work.

---

### Post by Xtensity on 2011-10-24
Results from boot script

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Testdisk is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdf.

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sda4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdf2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdf5 starts 
                       at sector 42. But according to the info from fdisk, 
                       sdf5 starts at sector 467884242.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2          20,996,955   544,458,751   523,461,797   7 NTFS / exFAT / HPFS
/dev/sda4    *    606,525,440   781,422,591   174,897,152  83 Linux


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
25 heads, 42 sectors/track, 465140 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *             63   467,884,031   467,883,969   7 NTFS / exFAT / HPFS
/dev/sdf2         467,884,200   488,395,949    20,511,750   f W95 Extended (LBA)
/dev/sdf5         467,884,242   488,395,949    20,511,708   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        01CC6A8077E20100                       ntfs       
/dev/sda4        38bf5145-3cc5-429e-abc6-962a683342ea   ext3       
/dev/sdf1        741877261876E710                       ntfs       
/dev/sdf5        181C70E01C70BA78                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda4/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 38bf5145-3cc5-429e-abc6-962a683342ea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 38bf5145-3cc5-429e-abc6-962a683342ea
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 38bf5145-3cc5-429e-abc6-962a683342ea
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=38bf5145-3cc5-429e-abc6-962a683342ea ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 38bf5145-3cc5-429e-abc6-962a683342ea
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=38bf5145-3cc5-429e-abc6-962a683342ea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 38bf5145-3cc5-429e-abc6-962a683342ea
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=38bf5145-3cc5-429e-abc6-962a683342ea ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 38bf5145-3cc5-429e-abc6-962a683342ea
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=38bf5145-3cc5-429e-abc6-962a683342ea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 38bf5145-3cc5-429e-abc6-962a683342ea
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 38bf5145-3cc5-429e-abc6-962a683342ea
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 16EC3FACEC3F8551
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 01CC6A8077E20100
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdg5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 6ad20eac-fb8f-4ab6-8646-0658b81a55c2
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6ad20eac-fb8f-4ab6-8646-0658b81a55c2 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdg5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 6ad20eac-fb8f-4ab6-8646-0658b81a55c2
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=6ad20eac-fb8f-4ab6-8646-0658b81a55c2 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda3 during installation
UUID=38bf5145-3cc5-429e-abc6-962a683342ea  /            ext3  errors=remount-ro    0  1  
# swap was on /dev/sdf6 during installation
UUID=ebae4a54-877f-460f-a5c5-2e2bed8bb282  none         swap  sw                   0  0  
# swap was on /dev/sdf8 during installation
UUID=1a59d303-e436-4109-9b57-3e85b7663009  none         swap  sw                   0  0  
/dev/sdf5                                  /media/sdf5  ext4  defaults             0  0  
/dev/sdf1                                  /media/sdf1  ntfs  defaults             0  0  

--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 315.737327576 = 339.020374016  boot/grub/core.img                             1
 315.853961945 = 339.145609216  boot/grub/grub.cfg                             1
 315.776607513 = 339.062550528  boot/grub/stage2                               3
 315.834655762 = 339.124879360  boot/initrd.img-2.6.35-22-generic              7
 315.853954315 = 339.145601024  boot/initrd.img-2.6.35-30-generic              4
 315.803855896 = 339.091808256  boot/vmlinuz-2.6.35-22-generic                 3
 315.843650818 = 339.134537728  boot/vmlinuz-2.6.35-30-generic                 4
 315.853954315 = 339.145601024  initrd.img                                     4
 315.834655762 = 339.124879360  initrd.img.old                                 7
 315.843650818 = 339.134537728  vmlinuz                                        4
 315.803855896 = 339.091808256  vmlinuz.old                                    3

================================ sdf1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(2)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(2)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 


```

---

### Post by Quackers on 2011-10-24
I would suggest re-installing grub to the mbr of the drive (/dev/sda, if that's the drive your bios boots from) in order to get your installed Ubuntu version booting.
Leave the wubi installation until later. That may boot anyway, but I am not familiar with wubi installations.

To re-install grub please copy/paste the following into a terminal on the live cd/usb desktop. Press enter after each line. ```
sudo mount /dev/sda4 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
```
This should report no errors.
If that's ok, reboot and you should see Ubuntu booting directly.
If it does, open up a terminal and run ```
sudo update-grub
``` when you should see the Windows Loader for /dev/sda2 (and possibly one for /dev/sdf1 as well, which appears to be a XP installation).
If they appear as grub.cfg is run, reboot and from the new grub menu try and boot everything in turn.

---

### Post by Xtensity on 2011-10-24
> **Quackers said:**
> I would suggest re-installing grub to the mbr of the drive (/dev/sda, if that's the drive your bios boots from) in order to get your installed Ubuntu version booting.
Leave the wubi installation until later. That may boot anyway, but I am not familiar with wubi installations.

To re-install grub please copy/paste the following into a terminal on the live cd/usb desktop. Press enter after each line. ```
sudo mount /dev/sda4 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
```
This should report no errors.
If that's ok, reboot and you should see Ubuntu booting directly.
If it does, open up a terminal and run ```
sudo update-grub
``` when you should see the Windows Loader for /dev/sda2 (and possibly one for /dev/sdf1 as well, which appears to be a XP installation).
If they appear as grub.cfg is run, reboot and from the new grub menu try and boot everything in turn.

Thankies very much... that worked. I'm still confused on why Boot-Repair program didn't work as it was supposed to do the same thing... oh well.

Now, so I don't **** everything up again... you wouldn't happen to know how I can make a partition that WindowsXP installation disc can see in order to install on, while in ubuntu? I figured having a clean NTFS file system or unpartitioned data would allow the XP disc to see it and use that to install on... but apperently not.

---

### Post by Quackers on 2011-10-24
Isn't XP installed on /dev/sdf1?

---

### Post by Xtensity on 2011-10-24
> **Quackers said:**
> Isn't XP installed on /dev/sdf1?

No... that's the removable hardrive my friend gave me, just has a bunch of files on it. It's formated NTFS

Besides, I wouldn't want XP on a removeable drive... Too risky for the $$$ files I'm dealing with. I need to figure out why XP Install disc cant see any of the partitions I create for it, or freeup, in ubuntu.

---

### Post by Quackers on 2011-10-24
Ah, I see :-)
Firstly, if you now install XP it will over-write grub, so the instructions you just used will have to be used again.
To be honest, it's so long since I used XP that I can't remember what is preferrrable for its installation.
I would have thought that a NTFS partition, or some unallocated space should be enough. I don't know why the install disc is not recognising these things on your system. 
The only thing I would say is that the NTFS partition may work better if it's created by Windows rather than gparted. Windows can be funny like that ;)

---

### Post by WasMeHere on 2011-10-24
Hi Xtensity,

I'm very glad to read that you managed to get your system bootable again :-) and I suggest that you wait a while to think about what to install into your computer.

If you will be using Windows XP very seldom, and only for a couple of applications, consider installing it in a virtual machine under Ubuntu! I run XP in Sun VirtualBox. With 'Guest Additions' it runs very smoothly and it will not cause any trouble of dual booting.

The other option, that I would suggest is the one already suggested by *OneXero*: Save your valuable files and do a clean reinstall! First make partitions: Prepare the first primary partition for Windows XP, and make an extended partition with logical partitions for Ubuntu. After that you should always start installing the least intelligent system (Windows XP) and then continue with Ubuntu. This way dual booting will work out of the box.

Have fun :-)
Olle

---

### Post by OneXero on 2011-10-24
> **Olle Wiklund said:**
> Hi Xtensity,

I'm very glad to read that you managed [..]
Olle


Yes! I didn't know how to phrase it, but that is very good. Least intelligent first ;). The stupid ones tend to smash everything in their way.

---

### Post by westie457 on 2011-10-24
@ Xtensity. Is your hard drive Sata or Ide? Only asking because XP when it first came out needed 3rd Party drivers to install to a Sata hard drive. Also if my memory is working correctly with Windows installations multi-booting they have/had to be installed with the oldest version first. This would mean wiping the hard drive installing XP then Windows 7 to its own partition then installing whatever else into extended partitions.

In all honesty the best way for you to go is follow Olle Wiklund's advice and install XP to a virtual machine. You will have play around a bit when setting up the virtual drive to behave like an Ide drive.

---

