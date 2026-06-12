---
title: "Windows 7 Grub2 OS-Prober Entry"
date: 2011-03-12
forum: General Help
---

### Post by flouran on 2011-03-12
Hi all,

I recently ran the update manager for my Ubuntu 10.10 system and when I rebooted I noticed that my Windows 7 entry was gone! I ran os prober, and it did not locate my Windows 7 partition. Thus, I decided to manually enter my Windows 7 entry by adding it to /etc/grub.d/40_custom as follows:
```

menuentry "Windows 7"{
set root=(hd0,3)
chainloader +1
}

```
However, when I rebooted my computer and selected the Windows 7 entry I had created I was given the following error message:
```

BOOTMGR is missing
Press Ctrl+Alt+Del to reboot

```
At first, I thought my Windows boot manager was corrupted. But this was not the case because I used the Windows system repair disk, and in the command line ran
```

bootrec /fixmbr

```
to make the Windows 7 bootmanager the default bootloader. And everything booted properly (I am currently writing this post from my Windows partition).

Anyway, I do recall back when the OS prober for Grub2 did recognize my Windows partition, the entry for it was much more complicated than a simpler chainloader +1 command. Thus, I was wondering if anyone could post the entry that they have for Windows 7 (or XP) that Grub2 automatically detected? Thanks.

---

### Post by coffeecat on 2011-03-12
You needed to run 'bootrec /fixboot' to restore the missing bootmgr file, not 'bootrec fixmbr' which writes Windows code to the mbr and replaces the grub code that was there. But since Windows is now booting OK, I guess that bootrec does a fixboot as well when you run fixmbr - which is interesting.

It's likely that the os-prober didn't detect Windows because of the missing bootmgr file, so if you now re-install grub and then run 'sudo update-grub' from within Ubuntu, you may find that you get an entry for Windows 7.

But rather than speculate, let's do some diagnostics. Run the live Ubuntu CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file in code tags. That should tell all.

Fwiw, the os-prober generated stanza for my Windows 7 is:

```
menuentry "Windows 7 on sda1" {
   insmod part_msdos
   insmod ntfs
   set root='(hd0,msdos1)'
   search --no-floppy --fs-uuid --set 4c54a5a254a58ef0
   chainloader +1
}
```I believe you don't actually need the UUID, but it's safer. But you do need the 'insmod ntfs' and 'nsmod part_msdos' lines.

However, I'd be surprised if os-prober doesn't do its thing now that bootmgr is (probably) back where it should be.

---

### Post by flouran on 2011-03-12
Here is my RESULTS.txt file (I only included the relevant partitions):
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         662,199,361   976,768,064   314,568,704   5 Extended
/dev/sda5         662,199,363   714,619,394    52,420,032   7 HPFS/NTFS
/dev/sda6         714,619,458   723,535,469     8,916,012  82 Linux swap / Solaris
/dev/sda7         723,535,533   976,768,064   253,232,532  83 Linux
/dev/sda2    *             63       208,844       208,782   7 HPFS/NTFS
/dev/sda3    *        208,845   335,742,434   335,533,590   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        AE585E9F585E65DD                       ntfs       SYSTEM RESERVED               
/dev/sda3        04ECBC75ECBC631A                       ntfs       Gateway                                               
/dev/sda5        45E48A0043FF2307                       ntfs       Data                          
/dev/sda6        3b95dd21-7f50-4670-ab7a-786b4215f0c2   swap       swap                          
/dev/sda7        addb5e11-7365-4b16-b978-e2e28353e982   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
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
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=addb5e11-7365-4b16-b978-e2e28353e982 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set addb5e11-7365-4b16-b978-e2e28353e982
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###

### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=addb5e11-7365-4b16-b978-e2e28353e982 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3b95dd21-7f50-4670-ab7a-786b4215f0c2 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 428.5GB: boot/grub/core.img
 483.1GB: boot/grub/grub.cfg
 428.7GB: boot/initrd.img-2.6.32-24-generic
 428.8GB: boot/initrd.img-2.6.32-25-generic
 430.6GB: boot/initrd.img-2.6.32-26-generic
 430.6GB: boot/initrd.img-2.6.32-27-generic
 430.6GB: boot/initrd.img-2.6.32-28-generic
 430.7GB: boot/initrd.img-2.6.32-29-generic
 390.9GB: boot/vmlinuz-2.6.32-24-generic
 428.8GB: boot/vmlinuz-2.6.32-25-generic
 430.6GB: boot/vmlinuz-2.6.32-26-generic
 430.6GB: boot/vmlinuz-2.6.32-27-generic
 430.6GB: boot/vmlinuz-2.6.32-28-generic
 430.6GB: boot/vmlinuz-2.6.32-29-generic
 430.7GB: initrd.img
 430.6GB: initrd.img.old
 430.6GB: vmlinuz
 430.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 00  00 00 c0 dd 1f 03 00 fe  |................|
000001d0  ff ff 05 fe ff ff c2 dd  1f 03 6b 0c 88 00 00 00  |..........k.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda6

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200

Unknown BootLoader  on sda4

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb ff 02 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf ed  e1 e8 6a 00 8a 16 04 e6  |.|h.N.....j.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5b 00 f4 eb fd 66 60  |.... ....[....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 52 31 d2 66 c1 ea 04  |.fa.f`...R1.f...|
000000f0  8e c2 5b 1e 1e 66 03 0e  00 e6 66 51 06 53 30 e4  |..[..f....fQ.S0.|
00000100  50 68 10 00 8a 16 04 e6  89 e6 b4 42 cd 13 72 a5  |Ph.........B..r.|
00000110  89 ec 07 66 61 c3 66 60  57 be dd e3 e8 07 00 5e  |...fa.f`W......^|
00000120  e8 03 00 66 61 c3 bb 01  00 ac 3c 00 74 06 b4 0e  |...fa.....<.t...|
00000130  cd 10 eb f5 c3 66 60 ad  86 e0 ab 3c 00 74 23 89  |.....f`....<.t#.|
00000140  c1 ad 86 e0 80 3e 01 e4  58 74 14 09 c0 75 01 48  |.....>..Xt...u.H|
00000150  80 fc 00 77 0a 3c 41 72  06 3c 5a 77 02 04 20 ab  |...w.<Ar.<Zw.. .|
00000160  e2 df 66 61 c3 66 60 b2  00 66 8b 44 02 66 3b 45  |..fa.f`..f.D.f;E|
00000170  02 75 0f 80 3c 00 75 0a  66 8b 44 06 66 3b 45 06  |.u..<.u.f.D.f;E.|
00000180  74 48 77 44 72 3d 66 60  31 d2 87 f7 66 ad 66 89  |tHwDr=f`1...f.f.|
00000190  c1 87 f7 66 ad 66 39 c8  77 2e 72 27 87 f7 ad 89  |...f.f9.w.r'....|
000001a0  c1 87 f7 ad 80 f9 00 74  1f 39 c8 74 0b 77 07 fe  |.......t.9.t.w..|
000001b0  ce 89 c1 e9 02 00 fe c6  f3 a7 77 0c 72 05 88 f2  |..........w.r...|
000001c0  e9 07 00 fe ca e9 02 00  fe c2 88 96 14 00 80 fa  |................|
000001d0  00 66 61 c3 50 57 8b 3e  0a e6 57 47 47 49 49 b0  |.fa.PW.>..WGGII.|
000001e0  00 f3 aa 89 3e 0a e6 5d  89 2d 5f 58 c3 2f 62 6f  |....>..].-_X./bo|
000001f0  6f 74 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |ot............U.|
00000200

```
It should come as no surprise that Windows is installed as the MBR of /dev/sda since I ran /FixMBR. This can easily be reverted to GRUB being the MBR if I choose to reinstall GRUB.

I also tried running 'bootrec /fixboot' to replace the missing bootmgr file, and then I reinstalled grub, booted into Ubuntu and ran 'sudo update-grub' and the os-prober still did not recognize my Windows 7 partition. I also tried to input your OS prober generated stanza for Windows 7 and the error was that the partition (hd0,msdos3) does not exist (I replaced msdos1 in your code with msdos3 since my Windows partition is on /dev/sda3).

---

### Post by coffeecat on 2011-03-12
> **flouran said:**
> I also tried to input your OS prober generated stanza for Windows 7 and the error was that the partition (hd0,msdos3) does not exist (I replaced msdos1 in your code with msdos3 since my Windows partition is on /dev/sda3).

You have what looks like a separate Windows 7 boot partition on sda2. Windows C: is on sda3. Normally, when W7 is set up like this you boot from the boot partition, not the C: partition. You'll also need to change the UUID if you use that line.

I wonder if os-prober is having difficulty detecting your Windows partition because the partitions are not in order. Your first partition is sda2, with the extended partition which comes later as sda1. I've only ever had Windows on discs with partition tables in strict numerical order. Just a thought.

---

### Post by runeh76 on 2011-03-12
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Rushyang on 2011-03-12
It's perfectly okay if Windows Boot Manger has taken over on your MBR right now.. I suggest this..

instead of going for fixing GRUB again.. Go and install a freeware on windows 7 - "[EasyBCD]("http://neosmart.net/dl.php?id=1")".
Then start EasyBCD in windows 7 and follow the following simple steps..
Start EasyBCD
Go to Add New Entry > Linux/BSD > Choose Type: GRUB 2.0 > Give appropriate name for Ubuntu  entry > Click Add Entry

Go to Edit Boot Menu > Save Settings.

Otherwise you can follow this loooong tutorial if you want GRUB 2.0 to be prompted first...
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

It's your call.

---

### Post by wilee-nilee on 2011-03-12
> **coffeecat said:**
> You have what looks like a separate Windows 7 boot partition on sda2. Windows C: is on sda3. Normally, when W7 is set up like this you boot from the boot partition, not the C: partition. You'll also need to change the UUID if you use that line.

I wonder if os-prober is having difficulty detecting your Windows partition because the partitions are not in order. Your first partition is sda2, with the extended partition which comes later as sda1. I've only ever had Windows on discs with partition tables in strict numerical order. Just a thought.

I wonder why it is showing the bootflag on sda2 and sda3, I though this was impossible.

easybcd lol.

---

### Post by coffeecat on 2011-03-12
> **wilee-nilee said:**
> I wonder why it is showing the bootflag on sda2 and sda3, I though this was impossible.

Yes, I noticed that and thought it was impossible too. Curious.

---

### Post by Rushyang on 2011-03-14
> **wilee-nilee said:**
> 
easybcd lol.

why you had to write **lol** about it.. The guy was looking for a solution and it works perfect. :?:

---

### Post by harbulot on 2011-03-14
Hi,

I've seen a similar problem, which seems to be due to the ntfs packages preventing [FONT=Courier New]os-prober[/FONT] from finding the Windows 7 partition. ([FONT=Courier New]os-prober[/FONT] is what's used by [FONT=Courier New]update-grub2 [/FONT]to determine the type of the other partitions).

If [FONT=Courier New]sudo os-prober[/FONT] can't find your Windows 7 partition, uninstall all the ntfs-related package (sorry, I didn't investigate the cause of this problem more specifically), run [FONT=Courier New]os-prober[/FONT] again, it should find your Windows partition now. If it does, you can run [FONT=Courier New]update-grub2[/FONT] and then re-install the ntfs packages.

---

