---
title: "xp home won't load"
date: 2010-12-08
forum: General Help
---

### Post by tylrgamster14 on 2010-12-08
hello...

well i installed ubuntu 10.10 and no problems but when i tryed booting xp home the screen just gos black and then lights up and thats it...it won't do anything else :(

please help

---

### Post by argedion on 2010-12-08
You will have to give more information that what you have given us.

1. Are you Dual booting from 2 seperate drives? or are you dual booting from a single drive?

2.Have you tried going into safe mode with XP? 

3.Can you boot into Ubunutu or a Live environment and see your windows folders and ensure they are still there?

Here is a link to a boot script download and run this script and post it in here using # code tags.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Many people can help when they have more specifics of the exact problem

---

### Post by sikander3786 on 2010-12-08
+1 to [bootinfoscript]("http://bootinfoscript.sourceforge.net") output.

Subscribing.

---

### Post by tylrgamster14 on 2010-12-08
> **argedion said:**
> You will have to give more information that what you have given us.

1. Are you Dual booting from 2 seperate drives? or are you dual booting from a single drive?

2.Have you tried going into safe mode with XP? 

3.Can you boot into Ubunutu or a Live environment and see your windows folders and ensure they are still there?

Here is a link to a boot script download and run this script and post it in here using # code tags.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Many people can help when they have more specifics of the exact problem

1.duel booting from 1 drive

2.i can't,like i said when i click on load windows xp home the screen goes off comes back on then nothing happens..theres no windows xp loading screen or nothing

3.yes i can boot in to ubuntu and i can see all the folders for windows xp

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   233,535,064   233,535,002   7 HPFS/NTFS
/dev/sda2         233,535,486   390,721,535   157,186,050   5 Extended
/dev/sda5         233,535,488   384,579,583   151,044,096  83 Linux
/dev/sda6         384,581,632   390,721,535     6,139,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        EE9CB98C9CB95037                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ec402a94-42f2-4777-9267-ecca89909a8c   ext4                                     
/dev/sda6        9b27176f-c73b-47a8-b7c6-5254f19702fd   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

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
search --no-floppy --fs-uuid --set ec402a94-42f2-4777-9267-ecca89909a8c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set ec402a94-42f2-4777-9267-ecca89909a8c
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ec402a94-42f2-4777-9267-ecca89909a8c
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=ec402a94-42f2-4777-9267-ecca89909a8c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ec402a94-42f2-4777-9267-ecca89909a8c
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=ec402a94-42f2-4777-9267-ecca89909a8c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ec402a94-42f2-4777-9267-ecca89909a8c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ec402a94-42f2-4777-9267-ecca89909a8c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ec402a94-42f2-4777-9267-ecca89909a8c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ec402a94-42f2-4777-9267-ecca89909a8c ro single 
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
	search --no-floppy --fs-uuid --set ec402a94-42f2-4777-9267-ecca89909a8c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ec402a94-42f2-4777-9267-ecca89909a8c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ee9cb98c9cb95037
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ec402a94-42f2-4777-9267-ecca89909a8c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9b27176f-c73b-47a8-b7c6-5254f19702fd none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 156.2GB: boot/grub/core.img
 164.8GB: boot/grub/grub.cfg
 120.3GB: boot/initrd.img-2.6.35-22-generic
 120.4GB: boot/initrd.img-2.6.35-23-generic
 156.2GB: boot/vmlinuz-2.6.35-22-generic
 156.3GB: boot/vmlinuz-2.6.35-23-generic
 120.4GB: initrd.img
 120.3GB: initrd.img.old
 156.3GB: vmlinuz
 156.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  30 a2 68 04 f9 d6 47 27  40 31 0c 01 89 2b 0c 28  |0.h...G'@1...+.(|
00000010  ac 18 a6 e5 b0 17 f8 89  27 fc cc 4f 11 0f d8 78  |........'..O...x|
00000020  5a b1 f5 5e 8c 09 9a 47  01 f2 a5 2d 7c 3e 86 ad  |Z..^...G...-|>..|
00000030  a1 a5 93 e5 57 f7 32 03  e2 31 bc e9 01 03 5b f0  |....W.2..1....[.|
00000040  99 20 36 c8 29 5f 37 5b  57 f4 f6 3b 01 31 d1 02  |. 6.)_7[W..;.1..|
00000050  c9 79 2e c7 9b 60 4c 79  c1 f5 ef d4 69 a6 0f 85  |.y...`Ly....i...|
00000060  42 5c 0f 87 b9 97 fe 7b  1d 1e 8c 71 f0 1d 02 35  |B\.....{...q...5|
00000070  cc bf f2 02 c3 e8 7d 3a  cf a3 1c 55 08 9f 9d 54  |......}:...U...T|
00000080  f1 a1 53 50 87 cd 01 e7  46 d7 9f 7b af 6b 1d 00  |..SP....F..{.k..|
00000090  f9 e0 ba 22 1a da c9 f8  3d 52 72 de 6e de ff 45  |..."....=Rr.n..E|
000000a0  32 fd 89 f0 87 dc 1d 6f  bf 05 4e fa db e9 6c 68  |2......o..N...lh|
000000b0  9a f6 87 d1 f9 23 e6 37  35 08 9f 91 82 c8 b6 a9  |.....#.75.......|
000000c0  b1 f7 5f e0 8e f1 f2 31  aa 92 a6 af a2 35 7c cf  |.._....1.....5|.|
000000d0  38 c3 27 af f7 73 0f 68  40 5d 4a 65 8f af 6c 74  |8.'..s.h@]Je..lt|
000000e0  77 8c bf b2 a9 55 fa ba  f6 f6 ab b7 c4 33 3e cd  |w....U.......3>.|
000000f0  a2 22 16 d5 47 50 ea 10  f7 29 8e 9b 0e e1 71 d5  |."..GP...)....q.|
00000100  fb 57 b8 0e 42 2d ab db  aa cc 85 57 cf 53 c7 57  |.W..B-.....W.S.W|
00000110  d7 74 f9 77 5f 95 7e 1d  6f be 66 d3 5b ef e6 c1  |.t.w_.~.o.f.[...|
00000120  d5 04 d7 bf 36 8e 01 64  03 5a f7 67 e2 24 3e 45  |....6..d.Z.g.$>E|
00000130  fe d5 37 b2 88 b4 a9 be  b0 fb fe f5 f3 8d b1 15  |..7.............|
00000140  fa ac 6d 7d 35 7f 32 e2  db 38 4e 10 d2 7b 07 5c  |..m}5.2..8N..{.\|
00000150  fc f0 0e ae be 6d aa bd  fc 6c c6 d7 f3 e3 c7 46  |.....m...l.....F|
00000160  44 4a f2 38 ed 75 f0 65  55 7c 2b b9 7d 55 7c 40  |DJ.8.u.eU|+.}U|@|
00000170  7f 05 57 c8 f7 85 d7 b0  0e 43 a3 2e 47 d5 79 75  |..W......C..G.yu|
00000180  55 f3 ed aa aa db e3 dd  e5 df 5e f8 7c 2a 88 b5  |U.........^.|*..|
00000190  f2 1d 75 fa 65 7d 9b c3  ab c5 e3 2a af 3c fa 7b  |..u.e}.....*.<.{|
000001a0  cf 7a aa af 2d cf 10 68  fa fb 45 fc ea 1c f5 f3  |.z..-..h..E.....|
000001b0  54 3a 77 c4 2f f8 f2 78  7c 28 54 3c 4c d7 00 fe  |T:w./..x|(T<L...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 00 09 00 fe  |................|
000001d0  ff ff 05 fe ff ff c5 c1  00 09 3d b6 5d 00 00 00  |..........=.]...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by oldfred on 2010-12-08
It is probably a windows issue. Boot script looks normal and all the windows files look in the correct place. The windows boot loader just looks for which partition has windows (boot flag) and jumps to that partitions boot sector. All grub does is jump to the windows boot sector just like the windows boot loader.

I would first run chkdsk since boot files look ok. Run chkdsk several times, until no more errors are detected.
Then it that does not work run the windows repairs to udpate/refresh the boot files & boot sector to see it that will fix it.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

---

### Post by tylrgamster14 on 2010-12-08
i can't boot into windows xp home and i don't have any windows xp cds..

im on ubuntu right now thats the only OS that will load

i looked on the drive and i already see those 2 files in the i386 folder and in the root of c:\

---

### Post by oldfred on 2010-12-08
Yes the files look ok, but we have had several users with similar issues fix them, by updating everything. We are not sure what of the issues it may be.

You can run chkdsk from a Vista or win7 repair CD. But do not use it for any other windows repairs as it is not compatible.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by tylrgamster14 on 2010-12-08
im downloading the vista recovery disk so do i just burn it to cd and restart the pc...??

---

### Post by argedion on 2010-12-08
> im downloading the vista recovery disk so do i just burn it to cd and restart the pc...??

Yes burn it to a cd or use a program like unetbootin to put it on a USB Then boot to that disk

---

### Post by tylrgamster14 on 2010-12-08
> **argedion said:**
> Yes burn it to a cd or use a program like unetbootin to put it on a USB Then boot to that disk

i put it on a disk how do i use the test disk on it..???

---

### Post by argedion on 2010-12-08
at the command prompt type:

```
chkdsk c: /p/r 
```

---

### Post by tylrgamster14 on 2010-12-08
> **argedion said:**
> at the command prompt type:

```
chkdsk c: /p/r 
```




Im srry im not trying to be a pain or anything but you got to go through the steps like are you talking about in ubuntu termanal to enter the command...??

---

### Post by oldfred on 2010-12-08
I posted the Microsoft links, we are not really a windows support group, but try to help those dual booting. I have not used it but I think these are links on how  to get to the Recovery Enviroment command line and then you just need to run chkdsk. Ignore all the other Vista fixes, if you attempt any of them you will make things worse.
A XP install disk from your original install is what you really should be using. 

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)


[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

---

### Post by tylrgamster14 on 2010-12-09
could i use any windows xp home cd or do i have to have the one that was used to install xp on my pc....:???:

---

### Post by oldfred on 2010-12-09
You are not installing and just going to the recovery enviroment. I would try it with any XP disk.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

In addition to chkdsk, if that aline does not work:
FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.

---

### Post by Krytarik on 2010-12-09
Today I obviously keep on advising: try downgrading to GRUB version 1.;)
It helped me on a similar problem, although with Windows 7.

---

### Post by tylrgamster14 on 2010-12-09
> **oldfred said:**
> You are not installing and just going to the recovery enviroment. I would try it with any XP disk.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

In addition to chkdsk, if that aline does not work:
FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.

Thank you for this and i will try it out...i will reply wut happens....peace:D

---

### Post by tylrgamster14 on 2010-12-09
well i tryed it and it was a no go ...but for some reason it wouldn't let me move the files from the cd to the drive....??

but any ways thanks everyone for all the responses but i will just stick with ubuntu..

i rather just deal with windows xp later...way later  :lol:


But knowing me i will make ubuntu work the way i want it too ;) ;)


i got another question should i make another thread..?? or can i just ask here

---

### Post by oldfred on 2010-12-09
New Thread would be better as the title will draw those who may know more about your question.

When you get back to windows. 
Did you run the chkdsk?
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

---

### Post by tylrgamster14 on 2010-12-10
Thank you old fred for replying to me..

i reinstalled windows and everything is working


thank you:popcorn:

---

