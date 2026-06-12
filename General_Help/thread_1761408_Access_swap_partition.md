---
title: "Access swap partition"
date: 2011-05-18
forum: General Help
---

### Post by p.todorov on 2011-05-18
Hi, 
I`m new to ubuntu so in the installation process i selected a random partition without much thinking,
but i had some important files there .
Is there a way to access them?

---

### Post by Rubi1200 on 2011-05-18
Hi and welcome to the forums :-)

Please stop all activity that would involve reading or writing to the disk.

You need to get hold of a LiveCD to boot the computer and then download and run the boot info script. There is a link at the bottom of my post with instructions.

Post the results here so we can take a look at what is going on.

---

### Post by p.todorov on 2011-05-18
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    36,869,174    36,869,112  82 Linux swap / Solaris
/dev/sda2          36,869,236   160,810,649   123,941,414   f W95 Extended (LBA)
/dev/sda5          36,869,238    98,301,734    61,432,497   7 NTFS / exFAT / HPFS
/dev/sda6    *     98,301,798   160,810,649    62,508,852   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   105,064,447   105,062,400  83 Linux
/dev/sdb2         105,065,161   312,560,639   207,495,479   f W95 Extended (LBA)
/dev/sdb5         105,065,163   312,560,639   207,495,477   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CAA4BCB9A4BCA8F9                       ntfs       OLD 1
/dev/sda5        10AC2F2CAC2F0C32                       ntfs       Old 2
/dev/sda6        42394f52-ce27-4980-9a08-58f39a293435   swap       
/dev/sdb1        c53394a5-d8ca-4538-99bf-3528e02834bf   ext4       
/dev/sdb5        96ACCDB5ACCD8FE3                       ntfs       NEW

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/c53394a5-d8ca-4538-99bf-3528e02834bf ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=RB5I3U /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=RB5I3U-BAK 
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=c53394a5-d8ca-4538-99bf-3528e02834bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=c53394a5-d8ca-4538-99bf-3528e02834bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c53394a5-d8ca-4538-99bf-3528e02834bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c53394a5-d8ca-4538-99bf-3528e02834bf ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set caa4bcb9a4bca8f9
    drivemap -s (hd0) ${root}
    chainloader +1
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.134311676 = 17.324085248   boot/grub/core.img                             1
  26.165317535 = 28.094795776   boot/grub/grub.cfg                             2
   1.404926300 = 1.508528128    boot/initrd.img-2.6.35-22-generic              3
   1.573501587 = 1.689534464    boot/initrd.img-2.6.35-28-generic              1
  16.138309479 = 17.328377856   boot/vmlinuz-2.6.35-22-generic                 1
  16.132854462 = 17.322520576   boot/vmlinuz-2.6.35-28-generic                 1
   1.573501587 = 1.689534464    initrd.img                                     1
   1.404926300 = 1.508528128    initrd.img.old                                 3
  16.132854462 = 17.322520576   vmlinuz                                        1
  16.138309479 = 17.328377856   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ad 31 ea df ab 00 31 23  8b f7 e6 bf be e5 e7 9d  |.1....1#........|
00000010  b6 bb 29 30 a3 ad 1f 5b  da 11 3b 15 9d 6d ec 8d  |..)0...[..;..m..|
00000020  44 da 98 b6 93 03 65 1e  df 12 70 02 0f 8d e6 3c  |D.....e...p....<|
00000030  59 bc c3 17 52 97 ba 7d  aa de 93 90 05 da fc e7  |Y...R..}........|
00000040  9f 61 2e 31 d5 60 89 67  99 67 40 d0 d6 48 d9 4d  |.a.1.`.g.g@..H.M|
00000050  88 8d fa c0 07 c0 09 5e  00 f3 9e de 4e dd c4 99  |.......^....N...|
00000060  38 b6 a2 29 7e 8d fc e9  00 26 23 80 3e 12 29 df  |8..)~....&#.>.).|
00000070  d0 03 be 38 71 8b 5d bb  25 75 b0 3e 6c 0c 6f ea  |...8q.].%u.>l.o.|
00000080  07 97 24 1d c1 7c 59 b0  39 61 d4 2d b8 f7 e9 cc  |..$..|Y.9a.-....|
00000090  7d e3 35 fd 79 e4 a9 36  cc 54 3a a5 46 a0 d6 ce  |}.5.y..6.T:.F...|
000000a0  c8 8d ff 27 c8 80 0f 40  1e 00 35 e5 fc 71 f3 08  |...'...@..5..q..|
000000b0  b4 57 37 39 99 0a e3 2c  59 43 56 37 ce 79 ec d2  |.W79...,YCV7.y..|
000000c0  21 03 db 6d e0 c9 22 95  b0 da 88 14 df d9 40 05  |!..m..".......@.|
000000d0  80 0b 40 1e 80 30 e7 98  23 73 8d cd 4e 4a 01 c8  |..@..0..#s..NJ..|
000000e0  c8 b4 6a 46 f9 6f 40 81  f8 60 0b ff d9 75 ef eb  |..jF.o@..`...u..|
000000f0  df f2 b1 c7 26 12 5a aa  aa ca 8c cc 18 7b 7f cf  |....&.Z......{..|
00000100  3e a1 97 45 0b 73 9e 64  d8 e2 a1 49 07 84 b7 d2  |>..E.s.d...I....|
00000110  88 bf ee 7a e7 9e 61 33  8f 28 a3 ee c2 fc 1b a4  |...z..a3.(......|
00000120  00 4c 08 1f a2 00 d8 01  6e 73 44 eb 88 dc cc ca  |.L......nsD.....|
00000130  e8 fa 55 b4 9a 5d a3 db  e5 4f e7 a1 36 ce 85 f0  |..U..]...O..6...|
00000140  2f 1f 4b b9 65 96 c3 95  b6 aa 35 99 92 56 fd cf  |/.K.e.....5..V..|
00000150  b1 18 02 d3 78 74 93 6e  5a b4 74 3e c6 ee 80 3b  |....xt.nZ.t>...;|
00000160  00 6c 23 40 1f 6d e4 5e  74 65 95 6a 5b b6 0e 6f  |.l#@.m.^te.j[..o|
00000170  9d 0b 93 3c bc b2 c7 b8  39 e8 35 69 61 48 c9 f3  |...<....9.5iaH..|
00000180  d0 03 6f af 19 82 65 74  15 0d 8b 52 5a 1a ce 58  |..o...et...RZ..X|
00000190  ac 58 b1 bf d9 8e ec 53  c5 e5 00 77 77 7a c9 71  |.X.....S...wwz.q|
000001a0  d3 20 7d 30 ea 81 ad f9  ef 7e 7e c0 0f 7f 9e 5f  |. }0.....~~...._|
000001b0  0e 9c 7b 70 64 dc 7c 90  d7 c8 90 a3 db 67 00 01  |..{pd.|......g..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 b1 62 a9 03 00 fe  |...........b....|
000001d0  ff ff 05 fe ff ff b3 62  a9 03 73 cf b9 03 00 00  |.......b..s.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


So this is the result of the script

---

### Post by coffeecat on 2011-05-18
Hi. Rubi1200 pm'd me and asked me to have a look since he may not be able to post back for a while. We'll  both try and help you through this when we get time.

My first impresssions. You've installed Ubuntu 10.10 to partition sdb1, that's the first partition on the second hard drive, the 160GB one. Was that where your important files were? If so, the partition has been reformatted with the Linux ext4 filesystem and about 2.2GB of files have been written to it. The partition is approx 54GB in size and Linux filesystems scatter all their files throughout the available space, rather than bunching them together as in NTFS. Which means your files may or may not have been overwritten.

If sdb1 was where your files were, then it might be possible to rescue the partition itself with a utility called testdisk. One possible problem is that if the original NTFS or FAT32 (I'm guessing it was one of those) filesystem is overwritten with the ext4 filesystem, then it may not be possible to recover the original filesystem. In which case you would have to try another utility which comes with testdisk called photorec. This can recover certain types of individual files. 

Here's a useful link for you to read which tells you more about testdisk and photorec:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

I suggest you don't do anything yet until we've established your situation precisely. I too will be unavailable for a few hours, but both I and Rubi1200 will come back to this thread.

One little oddity in your boot script output. It says that grub is installed to the mbr of sda (your first drive) which is what I would expect, but that it "looks in partition 1 for (,msdos1)/boot/grub" which implies that it is looking in sda1, whereas it should be looking in sdb1 for boot/grub. I suspect there is a glitch in the bootscript which I notice is version 0.60 which has only just been released. Probably no matter at the moment because you have a more important issue to deal with, but I just wanted to make a note of this.

---

### Post by p.todorov on 2011-05-18
So the files i`m searching for are in the sda6 partition
the windows files are old simply the disk was not formated
and they`re just not deleted but the windos os i not working this are just old useless files

---

### Post by coffeecat on 2011-05-18
Interesting. Your boot script output is showing even more inconsistencies than I first noticed. Your swap partition is showing as variously sda1 and sda6 in different places. Also, the form of your /etc/fstab files is not what an Ubuntu installer would create - it's not using UUIDs.

This needs some more thinking about. I have to log off now. I will be back in a few hours.

---

### Post by Rubi1200 on 2011-05-18
Thanks coffeecat for jumping and helping :-)

p.todorov, I am going to try something now that coffeecat is an expert in; diagnosing problems like this.

I am going to summarize, in the form of a question, what we know so far. Please try and answer as clearly as possible. It will make things a lot easier for us in terms of helping you solve this.

1.>  in the installation process i selected a random partition without much thinking Do you mean you selected it as the root partition or something else like swap perhaps?

2. before asking on the forums, did you take any other actions like attempting to write to the partitions, use partitioning tools or the like?

3. > the windows files are old simply the disk was not formated
and they`re just not deleted but the windos os i not working this are just old useless files      Please explain this more clearly. Which disk was not formatted?

4. sda6 reveals a conflicting story. The blkid command says it is swap, fdisk says it is formatted as NTFS:
> /dev/sda6    *     98,301,798   160,810,649    62,508,852   7 NTFS / exFAT / HPFS5. as above, as coffeecat mentioned, you seem to have 2 swap partitions.

6. why is the boot flag, which only Windows needs, on sda6 which may/mamy not have been a swap/root partition?

7. sda1 is variously shown as a swap partition and an NTFS boot partition?

I hope coffeecat has some more ideas so let's wait and see what he says.

Finally, do you have backups of all imprtant data and do you have the Windows installation/recovery disk?

---

### Post by coffeecat on 2011-05-18
> **Rubi1200 said:**
> 
5. as above, as coffeecat mentioned, you seem to have 2 swap partitions.

Well, I don't know - it's all very perplexing. Partitions sda1 and sda6 are appearing as either the swap and NTFS partitions or the other way around in different parts of the boot script output.

> **Rubi1200 said:**
> 
I hope coffeecat has some more ideas so let's wait and see what he says.


Yes. Do some more investigating! :)

@p.todorov, first a comment and then I'm going to ask you to run some more stuff from the live CD. If your files were on what is now the swap partition, I'm more hopeful that you will be able to rescue them. A swap partition doesn't really have a filesystem as such, so hopefully the original filesystem and files will not have been overwritten yet. Of course, that is if the files are on what is now the swap partition. As you can see, it's difficult to see what's what from the boot script output.

I think it would be a good idea to run the earlier version of the bootscript. The old version gave odd results with Natty/11.04 which I presume is why the version you used - 0.60 - has been released. Since you are running Maverick/10.10 it would be useful to see what the 0.55 version of boot script makes of your setup - the 0.55 version works with Maverick. Here's the download link:

[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.55/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.55/)

Boot up the live 10.10 CD and download that and run it in the same way as the script you've already run and post the output. Please enclose the output between [noparse]```
 and [/CODE[/noparse] tags - it makes it easier to read. You can use the # icon in the message toolbar for this.

Also - there is some output in the bootscript which looks a bit like the output of fdisk but which isn't, and this is the bit that contradicts what the rest says. While you have the live CD running, post the output of this terminal command:

[code]sudo fdisk -lu
```While you're in the live CD session and have a terminal open, let's have the output of:

```
sudo blkid
```The blkid output is in the bootscript output but it would be useful to be sure there are no other discrepancies. When posting the output of fdisk and blkid, please enclose the output between [noparse][CODE] and [/CODE[/noparse] tags as before.

---

### Post by p.todorov on 2011-05-18
1. I selected it as a swap by mistake cause  was in a hurry but i did`n formated it
2. i saw in the ubuntu disk utility that i can chanche the partition format so i tried 
3. i haven`t always been the administrator on the computer so i guess the windows files are left from someone else
4. only sda1 the file system disk was formated non of the others is been formated
5. the 2 swap prartitions i can`t explain
6. i selected sda 6 as a swap disk but without formating it
7. don`t know sda1 was previously my widndows bootable hdd

no i do not have any backup disk of the windows cause i removed windows and then installed ubuntu

---

### Post by p.todorov on 2011-05-18
thanks for the help so far but can i get to you tomorow mornig with all the info cause the computer is used in a pub to play music and it is getting harder for me to restart it often cause the clients and my bos arn`t happy about it

---

### Post by coffeecat on 2011-05-18
> **p.todorov said:**
> can i get to you tomorow mornig with all the info

No problem. I've subscribed to this thread and I'll be notified when you post again.

> **p.todorov said:**
> 2. i saw in the ubuntu disk utility that i can chanche the partition format so i tried 

Don't try anything else. Trying to reformat it in disk utility will increase any damage done. You need to use testdisk and/or photorec but first we need to sort out which partition is which.

---

### Post by Rubi1200 on 2011-05-18
I am in agreement with coffeecat on this one. Don't try anything else. Get us the information when you can and we will take it from there.

---

### Post by p.todorov on 2011-05-19
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    36,869,174    36,869,112  82 Linux swap / Solaris
/dev/sda2          36,869,236   160,810,649   123,941,414   f W95 Ext d (LBA)
/dev/sda5          36,869,238    98,301,734    61,432,497   7 HPFS/NTFS
/dev/sda6    *     98,301,798   160,810,649    62,508,852   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   105,064,447   105,062,400  83 Linux
/dev/sdb2         105,065,161   312,560,639   207,495,479   f W95 Ext d (LBA)
/dev/sdb5         105,065,163   312,560,639   207,495,477   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        CAA4BCB9A4BCA8F9                       ntfs       OLD 1                         
/dev/sda2: PTTYPE="dos" 
/dev/sda5        10AC2F2CAC2F0C32                       ntfs       Old 2                         
/dev/sda6        42394f52-ce27-4980-9a08-58f39a293435   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c53394a5-d8ca-4538-99bf-3528e02834bf   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        96ACCDB5ACCD8FE3                       ntfs       NEW                           
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=RB5I3U /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=RB5I3U-BAK 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=c53394a5-d8ca-4538-99bf-3528e02834bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=c53394a5-d8ca-4538-99bf-3528e02834bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c53394a5-d8ca-4538-99bf-3528e02834bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c53394a5-d8ca-4538-99bf-3528e02834bf ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c53394a5-d8ca-4538-99bf-3528e02834bf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set caa4bcb9a4bca8f9
    drivemap -s (hd0) ${root}
    chainloader +1
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  28.0GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-22-generic
   1.6GB: boot/initrd.img-2.6.35-28-generic
  17.3GB: boot/vmlinuz-2.6.35-22-generic
  17.3GB: boot/vmlinuz-2.6.35-28-generic
   1.6GB: initrd.img
   1.5GB: initrd.img.old
  17.3GB: vmlinuz
  17.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ad 31 ea df ab 00 31 23  8b f7 e6 bf be e5 e7 9d  |.1....1#........|
00000010  b6 bb 29 30 a3 ad 1f 5b  da 11 3b 15 9d 6d ec 8d  |..)0...[..;..m..|
00000020  44 da 98 b6 93 03 65 1e  df 12 70 02 0f 8d e6 3c  |D.....e...p....<|
00000030  59 bc c3 17 52 97 ba 7d  aa de 93 90 05 da fc e7  |Y...R..}........|
00000040  9f 61 2e 31 d5 60 89 67  99 67 40 d0 d6 48 d9 4d  |.a.1.`.g.g@..H.M|
00000050  88 8d fa c0 07 c0 09 5e  00 f3 9e de 4e dd c4 99  |.......^....N...|
00000060  38 b6 a2 29 7e 8d fc e9  00 26 23 80 3e 12 29 df  |8..)~....&#.>.).|
00000070  d0 03 be 38 71 8b 5d bb  25 75 b0 3e 6c 0c 6f ea  |...8q.].%u.>l.o.|
00000080  07 97 24 1d c1 7c 59 b0  39 61 d4 2d b8 f7 e9 cc  |..$..|Y.9a.-....|
00000090  7d e3 35 fd 79 e4 a9 36  cc 54 3a a5 46 a0 d6 ce  |}.5.y..6.T:.F...|
000000a0  c8 8d ff 27 c8 80 0f 40  1e 00 35 e5 fc 71 f3 08  |...'...@..5..q..|
000000b0  b4 57 37 39 99 0a e3 2c  59 43 56 37 ce 79 ec d2  |.W79...,YCV7.y..|
000000c0  21 03 db 6d e0 c9 22 95  b0 da 88 14 df d9 40 05  |!..m..".......@.|
000000d0  80 0b 40 1e 80 30 e7 98  23 73 8d cd 4e 4a 01 c8  |..@..0..#s..NJ..|
000000e0  c8 b4 6a 46 f9 6f 40 81  f8 60 0b ff d9 75 ef eb  |..jF.o@..`...u..|
000000f0  df f2 b1 c7 26 12 5a aa  aa ca 8c cc 18 7b 7f cf  |....&.Z......{..|
00000100  3e a1 97 45 0b 73 9e 64  d8 e2 a1 49 07 84 b7 d2  |>..E.s.d...I....|
00000110  88 bf ee 7a e7 9e 61 33  8f 28 a3 ee c2 fc 1b a4  |...z..a3.(......|
00000120  00 4c 08 1f a2 00 d8 01  6e 73 44 eb 88 dc cc ca  |.L......nsD.....|
00000130  e8 fa 55 b4 9a 5d a3 db  e5 4f e7 a1 36 ce 85 f0  |..U..]...O..6...|
00000140  2f 1f 4b b9 65 96 c3 95  b6 aa 35 99 92 56 fd cf  |/.K.e.....5..V..|
00000150  b1 18 02 d3 78 74 93 6e  5a b4 74 3e c6 ee 80 3b  |....xt.nZ.t>...;|
00000160  00 6c 23 40 1f 6d e4 5e  74 65 95 6a 5b b6 0e 6f  |.l#@.m.^te.j[..o|
00000170  9d 0b 93 3c bc b2 c7 b8  39 e8 35 69 61 48 c9 f3  |...<....9.5iaH..|
00000180  d0 03 6f af 19 82 65 74  15 0d 8b 52 5a 1a ce 58  |..o...et...RZ..X|
00000190  ac 58 b1 bf d9 8e ec 53  c5 e5 00 77 77 7a c9 71  |.X.....S...wwz.q|
000001a0  d3 20 7d 30 ea 81 ad f9  ef 7e 7e c0 0f 7f 9e 5f  |. }0.....~~...._|
000001b0  0e 9c 7b 70 64 dc 7c 90  d7 c8 90 a3 db 67 00 01  |..{pd.|......g..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 b1 62 a9 03 00 fe  |...........b....|
000001d0  ff ff 05 fe ff ff b3 62  a9 03 73 cf b9 03 00 00  |.......b..s.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by p.todorov on 2011-05-19
And another thing a friend of mine suggested to me to preform a binary copy of the info on the swap partition could this work

---

### Post by coffeecat on 2011-05-19
The output from the earlier version of bootscript is showing the same anomalies, so we can discount a bug in the newer version. I think it would be helpful if I highlight them.

```

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

<snip>

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

```Then:

```

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    36,869,174    36,869,112  82 [COLOR=Red]Linux swap / Solaris[/COLOR]
/dev/sda2          36,869,236   160,810,649   123,941,414   f W95 Ext d (LBA)
/dev/sda5          36,869,238    98,301,734    61,432,497   7 HPFS/NTFS
/dev/sda6    *     98,301,798   160,810,649    62,508,852   7 [COLOR=Red]HPFS/NTFS[/COLOR]

```And:

```

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
[COLOR=Red]/dev/sda1        CAA4BCB9A4BCA8F9                       ntfs       OLD 1[/COLOR]                         
/dev/sda2: PTTYPE="dos" 
/dev/sda5        10AC2F2CAC2F0C32                       ntfs       Old 2                         
[COLOR=Red]/dev/sda6        42394f52-ce27-4980-9a08-58f39a293435   swap [/COLOR]                                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c53394a5-d8ca-4538-99bf-3528e02834bf   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        96ACCDB5ACCD8FE3                       ntfs       NEW                           
/dev/sdb: PTTYPE="dos" 

```The first part of the boot script and blkid both scan (so I believe) the partitions for filesystem. The middle section of code that I've reposted looks a bit like the output of fdisk, but is not quite right for fdisk, which is why I asked for the output of fdisk as well (which you haven't posted). fdisk doesn't scan partitions but merely reports the contents of the partition table. If that middle bit of the bootscript output is a reading of the partition table, then you have a mismatch between what the partition table says and what filesystems are actually in the partitions.

In summary, what is probably happening is that:

Partition table says sda1 = swap; sda6 = NTFS

But the actual filesystems are sda1 = NTFS; sda6 = swap

Which would mean that the partition you need to recover is probably sda6. The bootscript also shows unequivocally that Windows XP is in sda1, so I'm confident about that. **However**, there is evidence of partition table inconsistency. This is serious.

Which leads to the next question. Apart from the installation, what else did you do?

First:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
```This is saying the same as the 0.60 script reported. Grub is wrongly installed. It should be looking in partition 1 of sdb for /boot/grub. The installer should have defaulted to this. Did you choose some special option for grub in the installation? I can't work out how this could have happened.

Also:

```

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================
```I can see that you've edited /etc/fstab. You may be new to Ubuntu, but you're not new to Linux! :wink: Or did someone else do that?

I only bring all this up because the partition table inconsistency is serious and we need to know everything that happened.

---

### Post by p.todorov on 2011-05-19
So here is all i know for this computer there are two fisical drives one i the old 80 gb who was used a bootable hard i a while was bought a new hard 160 gb who is then used for a bootable hard and id had windows and i installed linux and slected an old partition which was used as storage for a swap drive

---

### Post by Rubi1200 on 2011-05-19
Hi,
looking over the script results again and trying to wrap my head around this, I have come to the following conclusion as to the best course of action in this situation.

I think you need to use a LiveCD and try and recover your data/partitions using Testdisk and Photorec.

First, try and recover anything important with Photorec:
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Then, once you have some if not all your data, use Testdisk to see if there is a chance to get the partitions back to their former state:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If all else fails, backup the data and reinstall.

I wish we could help you more, but this is something you need to do on your own.

Best of luck :-)

---

### Post by coffeecat on 2011-05-19
I agree with Rubi1200. 

Try photorec on the sda6 partition first. As this was (probably) the partition with the important files, and as it is now (probably) a swap partition, the files should still be there and recoverable with photorec. Be warned, though, that photorec assigns different filenames to recovered files. You do not get the original filenames.

Having done that and, hopefully, got a set of copies of the lost files onto an external drive, try testdisk. This should be able to recover your sda6 partition to whatever it was before you installed Ubuntu, and should also be able to deal with the partition table discrepancy in partition sda1. If it recovers sda6 successfully your files should be still there with the original filenames, but it's still worth running photorec first.

Use testdisk/photorec from the live CD. By the way, we never did determine this: can you boot up into the installed Ubuntu and can you boot up into Windows? If yes to both I suggest you still use the live CD for testdisk/photorec. Read through the links Rubi1200 posted and also the one I posted in post #4 before you start.

I must emphasise one big caveat. I'm slightly reluctant to advise this because we have not explained everything, in particular how the partition table came to be corrupted and how /etc/fstab came to be edited. I'm reluctant to advise any course of action until I'm in possession of all the facts and as I feel that I'm not in this case I'm not happy to be suggesting going ahead with testdisk.

Actually a couple more caveats. Editing a partition table (which is what testdisk will do) has the potential for things going wrong. As Rubi1200 said, backup what you can. You could also do a dd copy of sda6 as your friend suggested - I am sure he can advise you how to do this. Lastly - if testdisk restores the correct partition table entry for Windows in sda1 this will be good but again there is the potential for things to go wrong. I'm not saying they will, just that you should be aware of this.

---

### Post by p.todorov on 2011-05-19
So this will sound very funny but i have trouble with the instalation and runing the program could you explain it for dummies please

---

### Post by coffeecat on 2011-05-19
I can't explain how to run testdisk and photorec any more clearly than is explained in the links Rubi1200 and I posted. Rubi1200's links are more comprehensive; the link I posted (post #4) is not so comprehensive but is perhaps a little easier to follow.

Sorry if this sounds unhelpful, but with both photorec and testdisk you need to read the documentation carefully so that you have some understanding of the process. Photorec isn't that difficult - once you've told it which partition to scan and a medium to write rescued files to, it will just get on with the job.

---

### Post by Rubi1200 on 2011-05-19
I agree with coffeecat that we really don't seem to have the whole picture here. I am also not entirely comfortable with the solution to use Testdisk. 

However, we do want you to be able to try and at least recover some of the data. To that end, Photorec is probably one of the best tools available. 

There are other recovery options such as professional software and data recovery services that specialize in this type of situation. Be aware, though, that such a service can cost into the thousands of pretty much any strong currency you choose to think of (dollars, pounds etc.).

The links we provided give the best idea of how to approach this, but here is another one too:
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

First recover and backup as much as you can before using Testdisk. Once you start running it, you can always post here and ask us for more advice about whatever it finds. In other words, don't write any changes to the partitions until you ask us if what it found is correct (as much as that can possibly be a safe assumption with such tools).

Good luck!

---

