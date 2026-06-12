---
title: "windows xp/linux boot prob.."
date: 2010-11-29
forum: General Help
---

### Post by jp351 on 2010-11-29
ok, so i use ubuntu 9.10 regularly, but from time to time i need to use windows for certain programs that i can't yet get to work on linux. i have a 500gb hard drive which i have a 16gb partition for windows and those programs. the problem is, recently i had to reinstall windows because it was errored like i've never seen before. however, now when i boot my computer, i can't choose which OS (or kernel) to boot from as it boots windows automatically. i'm pretty sure my linux OS is still there since i looked at the hdd properties, and 16gb was listed as the capacity of the hdd. 

when i checked in the start up / recovery options in the system properties, there's no other OS'es available for "default" and i do have the "time to display list of OS" checked and set to 15 seconds... but like i said, when i boot the computer, it boots windows automatically. 

anyone have any ideas/suggestions???

thanks :)

---

### Post by Tlingit on 2010-11-29
For a really easy solution I would just go and download a copy of super grub. Its a Grub master for your situation! It's its own Linux distro intended for live boot only.

Second suggestion wold to be pop your distro disk back in and manually fix it.
```
after booted "google" how to reinstall grub
```

What happened is windows erased grub and installed its own boot loader. I know there is another method you can use through windows, but haven't messed with it until windows vista came out.

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by jp351 on 2010-11-29
so i can use the super grub thing and it'll just reinstall the grub itself and it won't mess with either OS?

---

### Post by wilee-nilee on 2010-11-29
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by jp351 on 2010-11-29
ok, quick question, my mobo doesn't allow booting through a usb drive and i don't want to have a cd in the drive at all times to do this, is it easy to simply restore the GRUB to how it was before and let it be? as in, will it be the same as before reinstalling windows with the same menus and such?

---

### Post by wilee-nilee on 2010-11-29
> **jp351 said:**
> ok, quick question, my mobo doesn't allow booting through a usb drive and i don't want to have a cd in the drive at all times to do this, is it easy to simply restore the GRUB to how it was before and let it be? as in, will it be the same as before reinstalling windows with the same menus and such?

Post the bootscript and we will know.

---

### Post by Tlingit on 2010-11-29
> **jp351 said:**
> ok, quick question, my mobo doesn't allow booting through a usb drive and i don't want to have a cd in the drive at all times to do this, is it easy to simply restore the GRUB to how it was before and let it be? as in, will it be the same as before reinstalling windows with the same menus and such?

Yes like you said before you knew windows was not gone, and I said windows erased grub(and installed its own) so all the grub disk will do is fix YOUR Master Boot Record, and install grub.

Didn't follow what wilee-nilee said but you might want to go for his instructions first.

other then that 
```
My instructions will work unless you want some command line instructions. We are trying to repair your MBR to accommodated your set up and nothing else will be altered.
```


```
Google grub
```
```
MBR
```

---

### Post by jp351 on 2010-11-29
i don't think i can. i put the ubuntu disc i have in the drive, but it still booted right into windows. 

..i just want to restore GRUB.. i didn't think it'd be this hard to do..:(:|:x:-?:evil::x:x:x

---

### Post by Tlingit on 2010-11-29
Make sure your BIOS is set to boot from a cd.... Alter the BIOS settings to boot from cd you will have to probably press a button to not only get into the BIOS settings but also grab the boot device menu.

This is why I pointed you to SuperGrub, "It can be this hard to restore grub if you have no clue".

after you figure out how to alter your bios settings and boot back on to your live CD. Follow this tutorial

```
google restore grub
```

it will be the first link

---

### Post by matt_symes on 2010-11-29
Hi

Check the boot order in your BIOS. You want the first bootable item to be the CDRom. Check this is the case.

It might very well just be a case of reinstalling grub in the master boot record, however for the definitive answer it is best to follow willie-nillie's advice because it might be more than that. He knows what he is talking about.

However if you 100% sure can you follow the instructions here

[http://ubuntuforums.org/showthread.php?t=1627815&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=1627815&highlight=reinstall+grub)

You will need to identify the partition you have Ubuntu installed on and change sda5 in the post to that number.

The boot script would have given us that value straight away and also identified any other potential issues.

Kind regards

---

### Post by jp351 on 2010-11-30
ok, so i got it, but it told me that everything was in a text file, so do i still need to put it in code?

---

### Post by matt_symes on 2010-11-30
Hi

Follow these instructions from the site

How to use the boot info script  
[LIST]
[*] Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
[*]  [                                                 Download the Boot Info Script ]("http://sourceforge.net/projects/bootinfoscript")
[*] Open a terminal (Applications>Accessories>Terminal in Gnome) and type           sudo bash [path/to/the/download_folder]/boot_info_script*.sh  For example if you downloaded the file to the desktop, use          sudo bash ~/Desktop/boot_info_script*.sh
[*] If your operation system does not use sudo, use              su 
     bash ~/Desktop/boot_info_script*.sh
[*]You will now have the file RESULTS.txt in the same directory as     the script.[SIZE=-1] But if the script is inside a system directory (like     /usr or /etc) RESULTS.txt will be in the home directory.[/SIZE]
[*] If you already have an existing RESULTS.txt, subsequent  files will be called RESULTS1.txt, RESULTS2.txt,...
[*] Open RESULTS.txt in your favorite text editor.
[*] If you came here from a Linux forum, paste the content of  RESULTS.txt into your next post. Make sure to use the appropriate  formating.   For example in the Ubuntu forums click on the code tags (the symbol #)  before pasting RESULTS.txt.
[/LIST]
Kind regards

---

### Post by jp351 on 2010-11-30
if possible, can anyone tell me how to remove the (31-14) & (31-14 recovery) and the memtest86+ serial console from the list? i've tried using ubuntu tweak for it, but i can't find it anywhere on there. i have OCD so things like that being messy irritates me to no end.

thanks.


is it required to paste that in code? i can edit it if necessary.. i'll do that now... ok done.

---

### Post by jp351 on 2010-11-30
kk, so here's the code for it.. for whatever u need to use it..

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x47534752

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    31,423,139    31,423,077   7 HPFS/NTFS
/dev/sda2          31,423,140   976,768,064   945,344,925   5 Extended
/dev/sda5          31,423,203   969,249,644   937,826,442  83 Linux
/dev/sda6         969,249,708   976,768,064     7,518,357  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97cfabcc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4A88897B888965F3                       ntfs                                     
/dev/sda5        a6bf8f9c-f846-4607-b7d2-a9c32722d74d   ext4                                     
/dev/sda6        c075e96c-7f63-4878-9e50-0104235d4452   swap                                     
/dev/sdb1        2C106C8D106C5FB6                       ntfs       Slave                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda5        /media/a6bf8f9c-f846-4607-b7d2-a9c32722d74d ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda1        /media/4A88897B888965F3  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set a6bf8f9c-f846-4607-b7d2-a9c32722d74d
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set a6bf8f9c-f846-4607-b7d2-a9c32722d74d
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=a6bf8f9c-f846-4607-b7d2-a9c32722d74d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set a6bf8f9c-f846-4607-b7d2-a9c32722d74d
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=a6bf8f9c-f846-4607-b7d2-a9c32722d74d ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set a6bf8f9c-f846-4607-b7d2-a9c32722d74d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a6bf8f9c-f846-4607-b7d2-a9c32722d74d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set a6bf8f9c-f846-4607-b7d2-a9c32722d74d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a6bf8f9c-f846-4607-b7d2-a9c32722d74d ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 04e033cde033c428
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=a6bf8f9c-f846-4607-b7d2-a9c32722d74d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c075e96c-7f63-4878-9e50-0104235d4452 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  17.6GB: boot/grub/core.img
  17.6GB: boot/grub/grub.cfg
  16.7GB: boot/initrd.img-2.6.31-14-generic
  17.6GB: boot/initrd.img-2.6.31-22-generic
  16.7GB: boot/vmlinuz-2.6.31-14-generic
  16.5GB: boot/vmlinuz-2.6.31-22-generic
  17.6GB: initrd.img
  16.7GB: initrd.img.old
  16.5GB: vmlinuz
  16.7GB: vmlinuz.old

```

---

### Post by oldfred on 2010-11-30
Most of us suggest you keep two working kernels in the grub menu just incase something happens you have one to fall back to.

#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Then after rebooting:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions


Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by jp351 on 2010-11-30
i used the link and tried the "simple method: copy GRUB2 files from live CD"

i am currently running from the live CD.

after i did the "sudo grub-install" command in terminal, i got the following::

```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda5
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
```but of course, it helps to pay attention, instead of typing "sudo grub-install......./dev/sda5" i used "/dev/sda" and it worked.. i got the following...

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
```now i have to restart and update the GRUB2... i will report back with how it went..

---

### Post by jp351 on 2010-11-30
ok, i tried to update the grub, i'm not sure if i need to be in the actual linux OS, but i'm still using the live cd. i tried the update and got the following..

```
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

```

i'll restart without the liveCD and see what happens..

---

### Post by jp351 on 2010-11-30
WOOOOO it worked!!!

thanks guys!! :)

don't know why, but the update-grub command did nothing, however after i restarted, grub v1.97 beta loaded as it used to and everything was there as before.

now that i'm acutally IN linux, i did the update-grub command again and it updated the grub (i'm assuming).. readout is as follows::
```
chaos@chaos:~$ sudo update-grub
[sudo] password for chaos: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
```

again, thanks guys :)

---

