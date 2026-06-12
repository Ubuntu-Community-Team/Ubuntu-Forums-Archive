---
title: "In dire need of help - Ubuntu install, XP, etc."
date: 2011-01-14
forum: General Help
---

### Post by AmagicalFishy on 2011-01-14
Hello, ladies and gentlemen. First, please forgive any typos or faulty formatting -- I'm typing this on a PDA. It's the only form of internet I have until the library opens again (either tomorrow morning or Monday). About the extent of my problem, let me say this: I would now be in a sweaty, fearful panic if my heart were'nt made of steel covered in the frozen tears of children.

So, here's the deal:

I run Windows XP, SP2, and decided I wanted to try Ubuntu. I downloaded it and a few .deb packages at my school's library, came home, burned the ISO to a disk, and began the install of Ubuntu 10.10. I selected the "Install alongside another OS" option. This partition had about 50gb free, with the rest being taken up by XP and its various files. I was shown a little pictoral representation of how much space Ubuntu would take, apparently next to XP. I hit forward and continued, and the installation began. It froze at "Getting time from network server . . ." (or something to that extent). 

I turned the computer off, restarted, and planned to log into XP -- but the screen remained black with a little white blinking cursor. There were no boot options, just that. I tried then to boot from UBCD4Windows, but that froze after trying to load some files, leading me to believe some necessary Windows files were erased. My only option was to try to successfuly install Ubuntu.

I started the whole process over, but after the "install alongside other OS" screen, the diagram showed two Ubuntu installations (the one that had apparently been installed and the to-be installed). I went forward, and it froze again. I did this process a few times, messing w/ my hardware each time until I found the issue. (I had a network card, WN311b, but I don't have internet, and my username had a capital letter--though there was a green check next to it).

I also found that there were now 5 hidden partitions, so I chose where to install Ubuntu manually. The partitions were all named "dev/sd01" or "dev/sd05" (not exact). They matched the number of times I tried to install Ubuntu, so I deleted all but the largest (where I assumed my beloved XP was). Then I created a 50gb partition and a 1gb swap drive to install this one on.

The installation worked. Now I just need to get XP back before actually giving Ubuntu a shot. When I restart. I only get Ubuntu boot options. My XP disk doesn't have a recovery option on it, and I'm at a loss as to what to do.

I've rescued this comp. from BSODs that 90-percent of people recommended buying a new HD from, with all files intact and working, so I really hope there's a way of getting my stuff back. I'm sure there is, short of Ubuntu just overwriting all of my files (which I really hope it didn't do).

I am pretty computer literate, but Ubuntu is 100-percent foreighn to me. I tried playing a few games of solitaire, but that didn't fix anything. It's no stretch to say I very much value what was on the XP partition. If it's lost to me, there'll certainly be a moment of silence and a single tear.

Any help would very, very greatly be appreciated. Please note that I only have this (annoying, but sometimes handy) PDA with about 60mb of memory for internet access and downloading.

Thanks to anyone who read this. Gonna give my thumbs a break.

---

### Post by Quackers on 2011-01-14
Welcome to UF
It seems you can now boot Ubuntu, but you don't have internet access, is that correct? Do you have an ethernet cable and a router?

---

### Post by AmagicalFishy on 2011-01-14
I do, but I don't have internet. The reason I'm using this phone is because of th wireless plan. =/

---

### Post by Quackers on 2011-01-14
Then you are going to struggle to sort anything out. It's difficult to install anything to help you. 
Try looking at System > Admin > Disk Utility and see if the XP partition is still there. That's just about all I can think of. If you could download and run the boot script we would be able to help more, but as it is we're largely fishing in the dark. Even if we find out what's wrong, fixing it is likely to be near impossible, I would think, without internet access.

---

### Post by AmagicalFishy on 2011-01-14
It's "there", as in it's the correct size (205gb), but it's labelled as a Linux partition.

Also, I can download files up to 60mb on this phone, transfer them to the laptop (via USB), put it on a flash drive, and get it to my computer. It's a lot of work, but well worth it if it will help.

---

### Post by wilee-nilee on 2011-01-14
> **AmagicalFishy said:**
> It's "there", as in it's the correct size (205gb), but it's labelled as a Linux partition.

Also, I can download files up to 60mb on this phone, transfer them to the laptop (via USB), put it on a flash drive, and get it to my computer. It's a lot of work, but well worth it if it will help.

As Quackers suggest we need the boot script, your phone will up and download all the stuff, the only part may be getting all the text from the generated file to a post, the file to post is only about 13 or so Kib. 

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

You have run in the Ubuntu terminal this command correct, and scrolled through the full grub screen to see if XP is actually there.
```
sudo update-grub
```

---

### Post by AmagicalFishy on 2011-01-14
Phew! Here's the boot info:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   400,395,763   400,393,716  83 Linux
/dev/sda2         400,396,286   703,281,151   302,884,866   5 Extended
/dev/sda5         605,626,368   703,281,151    97,654,784  83 Linux
/dev/sda6         400,396,288   402,348,031     1,951,744  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 4051 MB, 4051697152 bytes
4 heads, 32 sectors/track, 61823 cylinders, total 7913471 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             32     7,913,470     7,913,439   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        43a3354e-07d7-4fc2-8f0d-67575d4ba023   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3ba3ee09-21dd-4bf6-9c8a-5fceb8d2e019   ext4                                     
/dev/sda6        604033fe-8de1-48d4-ac1f-f0ad5cda3861   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        4367-02A6                              vfat       MANDARIN                      
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/UBCD4Windows      iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdf1        /media/MANDARIN          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=32cf0bfa-ccd4-41ab-84cb-5eb61af000e5 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  51.6GB: boot/vmlinuz-2.6.35-22-generic
  51.6GB: vmlinuz

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3ba3ee09-21dd-4bf6-9c8a-5fceb8d2e019
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3ba3ee09-21dd-4bf6-9c8a-5fceb8d2e019
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 3ba3ee09-21dd-4bf6-9c8a-5fceb8d2e019
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3ba3ee09-21dd-4bf6-9c8a-5fceb8d2e019 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 3ba3ee09-21dd-4bf6-9c8a-5fceb8d2e019
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3ba3ee09-21dd-4bf6-9c8a-5fceb8d2e019 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 3ba3ee09-21dd-4bf6-9c8a-5fceb8d2e019
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 3ba3ee09-21dd-4bf6-9c8a-5fceb8d2e019
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 43a3354e-07d7-4fc2-8f0d-67575d4ba023
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 314.5GB: boot/grub/core.img
 334.0GB: boot/grub/grub.cfg
 310.4GB: boot/initrd.img-2.6.35-22-generic
 314.5GB: boot/vmlinuz-2.6.35-22-generic
 310.4GB: initrd.img
 314.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  aa 4d ce 03 77 98 38 ff  ed 43 4f af 8c f2 55 ce  |.M..w.8..CO...U.|
00000010  20 df 2a ef 18 66 f9 9f  de 0d b0 69 d3 8d f8 59  | .*..f.....i...Y|
00000020  aa 5c 06 d2 cf f4 51 3f  01 24 fd 6e ac e2 d7 14  |.\....Q?.$.n....|
00000030  39 69 de 6d d7 81 f1 7e  50 53 68 30 46 34 53 83  |9i.m...~PSh0F4S.|
00000040  bc 5b 83 52 78 b9 e1 64  8a 2e 40 60 88 b8 55 63  |.[.Rx..d..@`..Uc|
00000050  f6 d6 97 1e 06 ec 42 91  ad d6 fe b2 dc 74 b6 ae  |......B......t..|
00000060  5b a1 50 ef 3d ff d5 18  14 b6 84 ad 04 b4 c5 a2  |[.P.=...........|
00000070  87 37 5b 6f 14 4c 38 04  f7 a9 f4 dc 13 32 22 29  |.7[o.L8......2")|
00000080  7d 8c 79 cd fd ce e7 ad  73 8e 38 41 59 db 06 a4  |}.y.....s.8AY...|
00000090  ae 1c 25 d3 68 40 ee 11  0c 1d ce 73 c4 e3 f8 cb  |..%.h@.....s....|
000000a0  9e 33 53 d1 ee 94 ee 9a  0a 22 38 7c b8 7f 7f 15  |.3S......"8|....|
000000b0  7d 40 8f 97 08 c1 00 03  87 e0 a1 1f 2a 57 d9 c1  |}@..........*W..|
000000c0  dc fc c1 db 54 e5 c3 2e  55 c3 27 21 30 42 e3 a9  |....T...U.'!0B..|
000000d0  a4 e0 0a 0c bc 60 29 b0  b1 e0 8d 5e 3e 32 ae f1  |.....`)....^>2..|
000000e0  57 bd 0c 86 55 ca 5a 0c  86 4b 8f 87 fc e5 55 72  |W...U.Z..K....Ur|
000000f0  66 37 3e f4 fb bb ef be  ee fb 19 b7 dc ef b9 27  |f7>............'|
00000100  55 73 63 57 de 9f 7d ed  57 0c bc f0 27 19 89 76  |UscW..}.W...'..v|
00000110  33 6f 93 02 3a c2 6c 3e  80 aa 99 80 9a a9 71 7b  |3o..:.l>......q{|
00000120  39 db 56 05 b1 3b 03 ec  f0 63 d0 99 ac b4 f8 1f  |9.V..;...c......|
00000130  45 10 b3 7e 5f 9d f6 40  8a ee 3a 91 a0 da 38 06  |E..~_..@..:...8.|
00000140  c6 4c af 16 b5 c3 7d 1c  f6 ae fb fd 1b b8 96 49  |.L....}........I|
00000150  da 69 c6 1e 60 3e 6e cb  aa 9b de 42 93 c4 92 78  |.i..`>n....B...x|
00000160  0d a7 9d c2 8d d0 a4 cb  18 08 ad ac e1 b8 f8 77  |...............w|
00000170  f1 c5 b9 f6 8d 23 27 27  43 c9 60 64 7c 96 9b 52  |.....#''C.`d|..R|
00000180  09 a8 80 b0 37 b8 4d 46  2e 43 18 2e f7 8e 42 30  |....7.MF.C....B0|
00000190  cb a4 5c 9d dd c4 07 c6  b4 e0 c9 c3 53 b9 ce 69  |..\.........S..i|
000001a0  5c 18 30 4f d2 2b 9a ed  9f 84 c4 8f a5 bf 06 7e  |\.0O.+.........~|
000001b0  9e c3 1a d9 10 e1 a8 64  94 53 b9 cf 11 a6 00 fe  |.......d.S......|
000001c0  ff ff 83 fe ff ff 02 90  3b 0c 00 18 d2 05 00 fe  |........;.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 c8 1d 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

And the update-grub, after running the boot script (I did one before running it, too, but didn't save it):
```
jack@jack:~$ sudo update-grub
[sudo] password for jack: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done
jack@jack:~$ ^C
jack@jack:~$ ^C
jack@jack:~$ 


```

I uploaded the .txt files in case the paste didn't work as well as I wanted. I did notice that at the top of the RESULTS.txt, it says "WINDOWS is installed."

. . . That's good, yeah?

---

### Post by wilee-nilee on 2011-01-15
Are you sure that XP is still there, it looks like it has been overwritten to me. You have a sdf but it is very small 4 gigs. Can you open any XP partitions from Ubuntu? If XP is there it will be in the sidebar of the home in Ubuntu and places and computer. Install gparted in Ubuntu and open it and look to see if any NTFS partitions are there.

Is the sda1 partition a boot partition as well?

---

### Post by AmagicalFishy on 2011-01-15
Ok. I managed to install gparted after installing a libparted package and figuring out what "sudo" does--I finally understand that XKCD comic.

It doesn't look like there are any NTFS partitions, just ext3, extended, and linux-swap, which doesn't seem to be a good sign. The sda1 partition is bootable, but I can't login to it (that was the 1st install, and apparently it's stuck in some hellish limbo between asking for a Username and Pass, and not actually having one).

I'm not sure if XP is there or not; I'm a total linux newbie, though I assume if there are no NTFS partitions, it's not there, eh?

The "Windows is installed" line in RESULTS.txt is giving me hope, though. Can it be that some core files are missing or have been replaced w/ Ubuntu ones?

Is there a way of salvaging, at least, my files, even though I have to reinstall the OS? I can't see any Windows files when I try to explore that partition, but maybe that's because I'm not logged into it. . .or root?

---

### Post by wilee-nilee on 2011-01-15
> **AmagicalFishy said:**
> Ok. I managed to install gparted after installing a libparted package and figuring out what "sudo" does--I finally understand that XKCD comic.

It doesn't look like there are any NTFS partitions, just ext3, extended, and linux-swap, which doesn't seem to be a good sign. The sda1 partition is bootable, but I can't login to it (that was the 1st install, and apparently it's stuck in some hellish limbo between asking for a Username and Pass, and not actually having one).

I'm not sure if XP is there or not; I'm a total linux newbie, though I assume if there are no NTFS partitions, it's not there, eh?

The "**Windows is installed**" line in RESULTS.txt is giving me hope, though. Can it be that some core files are missing or have been replaced w/ Ubuntu ones?

Is there a way of salvaging, at least, my files, even though I have to reinstall the OS? I can't see any Windows files when I try to explore that partition, but maybe that's because I'm not logged into it. . .or root?

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs: 

Is this what this is, UBCD4Windows?  

If you have overwritten XP and have been using Ubuntu for awhile, I doubt much can be done. However there is a recovery called testdisk, and can be used from a booted Ubuntu cd.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It is tedious and unlikely to find stuff but you never know, this is not newbie area, so act accordingly. If you want any chance of recovery you have to not use the HD at all, at this point. 

To be honest you original description has to much information, we just want the basic facts, so I can't really tell how long you had Ubuntu working and just used it or at all really. This use after install systematically makes it unlikely that any recovery can be done the longer you use it. 

I can't really be of any help other then pointing you at testdisk, I have never used it.

---

### Post by AmagicalFishy on 2011-01-15
Ah. My apologies. I just tried to include as much info. as possible--though I suppose some of it was wholly uneccesary. I'm going to givr Testdisk a try. Thanks for your help :)

I'll post back if I manage anything!

---

### Post by AmagicalFishy on 2011-01-15
Haha!

Thanks again for your help, man. Testdisk did the trick. It found my Windows partition, restored the MBR, and some stuff and things. From there I ran a few cleanup programs on UBCD4Win, chksdk, and altered the registry a bit (though I don't know how much that helped). I was able to log onto XP--but it was like someone tore holes in random .dll files and programs (half of my Starcraft II folder was completely gone).

I backed up everything I needed, reformatted, and successfuly installed Ubuntu on a separate, manually created partition. Running fresh XP and Ubuntu 10.10 with all my files, so I'm a happy camper. You'll probably be seeing more of me when I get an internet connection.

Thanks again! :)

---

### Post by Quackers on 2011-01-15
Nice one, well done you and wilee-nilee :-)

---

### Post by wilee-nilee on 2011-01-15
> **AmagicalFishy said:**
> Haha!

Thanks again for your help, man. Testdisk did the trick. It found my Windows partition, restored the MBR, and some stuff and things. From there I ran a few cleanup programs on UBCD4Win, chksdk, and altered the registry a bit (though I don't know how much that helped). I was able to log onto XP--but it was like someone tore holes in random .dll files and programs (half of my Starcraft II folder was completely gone).

I backed up everything I needed, reformatted, and successfuly installed Ubuntu on a separate, manually created partition. Running fresh XP and Ubuntu 10.10 with all my files, so I'm a happy camper. You'll probably be seeing more of me when I get an internet connection.

Thanks again! :)

That is great, testdisk if used correctly in the right circumstances, seems to work what seems to be wonders.:)

---

