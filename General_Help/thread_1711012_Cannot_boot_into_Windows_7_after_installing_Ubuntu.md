---
title: "Cannot boot into Windows 7 after installing Ubuntu 10.10"
date: 2011-03-20
forum: General Help
---

### Post by Mikko8 on 2011-03-20
Basically what have I done so far:


[LIST=1]
[*]I had 2 separate partitions on my computer: one for Windows 7, one without a system on it.
[*]On the 2nd of the described partition at the end of it I installed Debian Linux. (After that I had 3 usable / visible partitions.)
[*]I was looking for less hassle with drivers so I decided to install Ubuntu and make greater the partition for Linux. In a forum I saw an article describing how to uninstall (remove) Debian. Roughly it described the process as follows:
[LIST=1]
[*]Delete Debian partition from Windows.
[*]Restart and in repair mode enter "repairmbr".
[/LIST]
 
[*]I did the first step. After the restart, the grub seemed to be damaged and it wouldn't show any options.
[*]Started the Ubuntu LiveCD, made the "Linux" partition greater, moved it to the beginning of the original of the to large partitions, transformed it to an extended partition, created the swap area in the beginning of it and installed Ubuntu 10.10.
[*]All went well, a new grub was created, Windows loader was detected, but didn't work. Same after upgraded to a newer version of Linux generic kernel. The installation process detected the Windows 7 but after restart it does not work. When trying to enter it, for about 1..2 seconds the screen turns black and again the same Grub menu is shown.
[/LIST]
[SIZE=2][COLOR=DarkRed]So the problem is that I cannot boot into Windows 7, I had pre-installed it so I don't have a disk for it. Recovery disks I made seems to be for re-installation only which is not an option at this time. All repair modes where accessible when starting Windows; any of them is not accessible.[/COLOR][/SIZE]

Both Windows 7 and Ubuntu 10.10 are 64-bit systems.

I will provide screenshots or other information if needed.

---

### Post by WlaadDyaab on 2011-03-20
> **Mikko8 said:**
> Basically what have I done so far:


[LIST=1]
[*]I had 2 separate partitions on my computer: one for Windows 7, one without a system on it.
[*]On the 2nd of the described partition at the end of it I installed Debian Linux. (After that I had 3 usable / visible partitions.)
[*]I was looking for less hassle with drivers so I decided to install Ubuntu and make greater the partition for Linux. In a forum I saw an article describing how to uninstall (remove) Debian. Roughly it described the process as follows:
[LIST=1]
[*]Delete Debian partition from Windows.
[*]Restart and in repair mode enter "repairmbr".
[/LIST]
 
[*]I did the first step. After the restart, the grub seemed to be damaged and it wouldn't show any options.
[*]Started the Ubuntu LiveCD, made the "Linux" partition greater, moved it to the beginning of the original of the to large partitions, transformed it to an extended partition, created the swap area in the beginning of it and installed Ubuntu 10.10.
[*]All went well, a new grub was created, Windows loader was detected, but didn't work. Same after upgraded to a newer version of Linux generic kernel. The installation process detected the Windows 7 but after restart it does not work. When trying to enter it, for about 1..2 seconds the screen turns black and again the same Grub menu is shown.
[/LIST]
[SIZE=2][COLOR=DarkRed]So the problem is that I cannot boot into Windows 7, I had pre-installed it so I don't have a disk for it. Recovery disks I made seems to be for re-installation only which is not an option at this time. All repair modes where accessible when starting Windows; any of them is not accessible.[/COLOR][/SIZE]

Both Windows 7 and Ubuntu 10.10 are 64-bit systems.

I will provide screenshots or other information if needed.

OK

I think the problem is the time Grub menu takes, before loading to the default Operating System

Could you please tell me what if it says "GRUB_TIMEOUT=10" or something else other than "10"

That's done through Terminal:

- Applications > Accessories > Terminal (short-cut: ctrl + alt + T)

- In "Terminal" copy/paste > sudo nano /etc/default/grub
- Press "Enter" (or "return key") > Type your password > Return key

Then look for "GRUB_TIMEOUT=...". Does it have a number other than "10" next to the equal sign?

If so, change it to "10" or whatever suits you

If you modified anything:

- Ctrl + X > Press "Y" on your keyboard > Press the return key
- Then copy-paste this > sudo update-grub
- Press return key

If you never modified anything:

- Just press Ctrl + X

Then restart your computer and it should now give you 10 seconds to allow you to either choose Ubuntu or Windows 7

Did that solve the problem?

---

### Post by Mikko8 on 2011-03-20
> **WlaadDyaab said:**
> ..

Then restart your computer and it should now give you 10 seconds to allow you to either choose Ubuntu or Windows 7

Did that solve the problem?

The Grub timeout was 10; it wasn't the problem.

The problem is that when the "Windows 7" loader line in Grub menu is selected it (the screen) turns black and again shows the Grub menu.

---

### Post by Mikko8 on 2011-03-21
Doesn't anyone know how to re-enable Windows 7 option within the Grub menu?

---

### Post by Rubi1200 on 2011-03-21
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Mikko8 on 2011-03-21
Here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 318166112 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   312,907,775   312,086,528   7 HPFS/NTFS
/dev/sda3         361,113,600   625,141,759   264,028,160   7 HPFS/NTFS
/dev/sda4         312,909,822   361,113,599    48,203,778   5 Extended
/dev/sda5         319,420,416   361,113,599    41,693,184  83 Linux
/dev/sda6         312,909,824   319,418,367     6,508,544  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5C087B12087AEA82                       ntfs       SYSTEM                        
/dev/sda2        1C227EFE227EDBE8                       ntfs       WINDOWS                       
/dev/sda3        0830810C308101C4                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        228757b1-bda2-460e-b803-07e5f3fe6b5c   ext4                                     
/dev/sda6        6ff70d2f-2984-4cbd-9fca-127373828dd9   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


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
search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=228757b1-bda2-460e-b803-07e5f3fe6b5c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=228757b1-bda2-460e-b803-07e5f3fe6b5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5c087b12087aea82
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
UUID=228757b1-bda2-460e-b803-07e5f3fe6b5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6ff70d2f-2984-4cbd-9fca-127373828dd9 none            swap    sw              0       0
# mount automatically WINDOWS partition
# /dev/sda2
/dev/sda2 /media/WINDOWS ntfs-3g defaults,locale=en_GB.utf8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 165.8GB: boot/grub/core.img
 181.8GB: boot/grub/grub.cfg
 165.1GB: boot/initrd.img-2.6.35-28-generic
 164.4GB: boot/vmlinuz-2.6.35-28-generic
 165.1GB: initrd.img
 164.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  78 00 64 00 00 00 00 00  f3 65 00 00 00 00 01 00  |x.d......e......|
00000010  d5 20 dd e4 68 71 cb 01  00 73 af 17 62 43 c9 01  |. ..hq...s..bC..|
00000020  d5 20 dd e4 68 71 cb 01  d5 20 dd e4 68 71 cb 01  |. ..hq... ..hq..|
00000030  60 00 00 00 00 00 00 00  5c 00 00 00 00 00 00 00  |`.......\.......|
00000040  20 00 00 00 00 00 00 00  11 01 4d 00 65 00 6e 00  | .........M.e.n.|
00000050  75 00 53 00 65 00 70 00  61 00 72 00 61 00 74 00  |u.S.e.p.a.r.a.t.|
00000060  6f 00 72 00 2e 00 78 00  6d 00 6c 00 00 00 00 00  |o.r...x.m.l.....|
00000070  1d 66 00 00 00 00 01 00  70 00 5a 00 00 00 00 00  |.f......p.Z.....|
00000080  f3 65 00 00 00 00 01 00  d5 20 dd e4 68 71 cb 01  |.e....... ..hq..|
00000090  00 73 af 17 62 43 c9 01  d5 20 dd e4 68 71 cb 01  |.s..bC... ..hq..|
000000a0  d5 20 dd e4 68 71 cb 01  60 00 00 00 00 00 00 00  |. ..hq..`.......|
000000b0  5c 00 00 00 00 00 00 00  20 00 00 00 00 00 00 00  |\....... .......|
000000c0  0c 02 4d 00 45 00 4e 00  55 00 53 00 45 00 7e 00  |..M.E.N.U.S.E.~.|
000000d0  31 00 2e 00 58 00 4d 00  4c 00 00 00 00 00 00 00  |1...X.M.L.......|
000000e0  1e 66 00 00 00 00 01 00  78 00 62 00 00 00 00 00  |.f......x.b.....|
000000f0  f3 65 00 00 00 00 01 00  d5 20 dd e4 68 71 cb 01  |.e....... ..hq..|
00000100  00 46 7e 16 62 43 c9 01  d5 20 dd e4 68 71 cb 01  |.F~.bC... ..hq..|
00000110  d5 20 dd e4 68 71 cb 01  98 00 00 00 00 00 00 00  |. ..hq..........|
00000120  95 00 00 00 00 00 00 00  20 00 00 00 00 00 00 00  |........ .......|
00000130  10 01 4d 00 65 00 6e 00  75 00 53 00 68 00 6f 00  |..M.e.n.u.S.h.o.|
00000140  72 00 74 00 63 00 75 00  74 00 2e 00 78 00 6d 00  |r.t.c.u.t...x.m.|
00000150  6c 00 00 00 00 00 00 00  1e 66 00 00 00 00 01 00  |l........f......|
00000160  70 00 5a 00 00 00 00 00  f3 65 00 00 00 00 01 00  |p.Z......e......|
00000170  d5 20 dd e4 68 71 cb 01  00 46 7e 16 62 43 c9 01  |. ..hq...F~.bC..|
00000180  d5 20 dd e4 68 71 cb 01  d5 20 dd e4 68 71 cb 01  |. ..hq... ..hq..|
00000190  98 00 00 00 00 00 00 00  95 00 00 00 00 00 00 00  |................|
000001a0  20 00 00 00 00 00 00 00  0c 02 4d 00 45 00 4e 00  | .........M.E.N.|
000001b0  55 00 53 00 48 00 7e 00  31 00 2e 00 58 00 00 fe  |U.S.H.~.1...X...|
000001c0  ff ff 83 fe ff ff 02 58  63 00 00 30 7c 02 00 fe  |.......Xc..0|...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 50 63 00 00 00  |...........Pc...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by Rubi1200 on 2011-03-21
Here is the problem:

> Grub 2 is installed in the boot sector of sda1sda1 is the Windows boot sector.

You have to first restore the Windows bootloader and then reinstall GRUB:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

EDIT:
just to be clear, you MUST install GRUB to the MBR of sda and not the partition.

---

### Post by Mikko8 on 2011-03-22
I did all you said but it doesn't seem to change anything. I tried to manualy change Grub but it was basically guessing. 

After failing in the atempts to correct the entry I run the test another time. There were two changes:
First:
```
============================= Boot Info Summary: ==============================

[COLOR=Purple]** => Windows is installed in the MBR of /dev/sda**[/COLOR]
```Second: This was due to guessing the settings:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda[COLOR=Purple]**2**[/COLOR])" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos[COLOR=Purple]**2**[/COLOR])'
    search --no-floppy --fs-uuid --set [COLOR=Purple]**7734184b-54ed-11e0-96d5-806e6f6e6963**[/COLOR]
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```The "[COLOR=Purple]**7734184b-54ed-11e0-96d5-806e6f6e6963**[/COLOR]" string I wrote down from Windows command prompt because I saw something similar in Grub for other entries. The difference was that after trying to boot with these settings there was a different response. The output on the screen said that the bootmanager is missing.

After this test I made other atempts to re-install Grub with different methods but it really doesn't seem that Grub is to blame. Just my guess but I think there is something wrong with the Windows part not Linux.

EDIT:
When run with these settings ...
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda[COLOR=Purple]**2**[/COLOR])" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos[COLOR=Purple]**2**[/COLOR])'
    search --no-floppy --fs-uuid --set [COLOR=Purple]**7734184b-54ed-11e0-96d5-806e6f6e6963**[/COLOR]
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```... I got this on my screen:
```
BOOTMGR is missing
Press Ctrl+Alt+Del to restart
```

---

### Post by Rubi1200 on 2011-03-22
Hi,
the best thing to do is run the boot info script again and post the entire contents here. Otherwise, it is just a guessing game about the current state of the system.

Thanks.

---

### Post by Mikko8 on 2011-03-22
> **Rubi1200 said:**
> Hi,
the best thing to do is run the boot info script again and post the entire contents here. Otherwise, it is just a guessing game about the current state of the system.

Thanks.

The most recent data:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   312,907,775   312,086,528   7 HPFS/NTFS
/dev/sda3         361,113,600   625,141,759   264,028,160   7 HPFS/NTFS
/dev/sda4         312,909,822   361,113,599    48,203,778   5 Extended
/dev/sda5         319,420,416   361,113,599    41,693,184  83 Linux
/dev/sda6         312,909,824   319,418,367     6,508,544  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5C087B12087AEA82                       ntfs       SYSTEM                        
/dev/sda2        1C227EFE227EDBE8                       ntfs       WINDOWS                       
/dev/sda3        0830810C308101C4                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        228757b1-bda2-460e-b803-07e5f3fe6b5c   ext4                                     
/dev/sda6        6ff70d2f-2984-4cbd-9fca-127373828dd9   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=228757b1-bda2-460e-b803-07e5f3fe6b5c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=228757b1-bda2-460e-b803-07e5f3fe6b5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 228757b1-bda2-460e-b803-07e5f3fe6b5c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5c087b12087aea82
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
UUID=228757b1-bda2-460e-b803-07e5f3fe6b5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6ff70d2f-2984-4cbd-9fca-127373828dd9 none            swap    sw              0       0
# mount automatically WINDOWS partition
# /dev/sda2
/dev/sda2 /media/WINDOWS ntfs-3g defaults,locale=en_GB.utf8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 165.8GB: boot/grub/core.img
 165.9GB: boot/grub/grub.cfg
 165.1GB: boot/initrd.img-2.6.35-28-generic
 164.4GB: boot/vmlinuz-2.6.35-28-generic
 165.1GB: initrd.img
 164.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  78 00 64 00 00 00 00 00  f3 65 00 00 00 00 01 00  |x.d......e......|
00000010  d5 20 dd e4 68 71 cb 01  00 73 af 17 62 43 c9 01  |. ..hq...s..bC..|
00000020  d5 20 dd e4 68 71 cb 01  d5 20 dd e4 68 71 cb 01  |. ..hq... ..hq..|
00000030  60 00 00 00 00 00 00 00  5c 00 00 00 00 00 00 00  |`.......\.......|
00000040  20 00 00 00 00 00 00 00  11 01 4d 00 65 00 6e 00  | .........M.e.n.|
00000050  75 00 53 00 65 00 70 00  61 00 72 00 61 00 74 00  |u.S.e.p.a.r.a.t.|
00000060  6f 00 72 00 2e 00 78 00  6d 00 6c 00 00 00 00 00  |o.r...x.m.l.....|
00000070  1d 66 00 00 00 00 01 00  70 00 5a 00 00 00 00 00  |.f......p.Z.....|
00000080  f3 65 00 00 00 00 01 00  d5 20 dd e4 68 71 cb 01  |.e....... ..hq..|
00000090  00 73 af 17 62 43 c9 01  d5 20 dd e4 68 71 cb 01  |.s..bC... ..hq..|
000000a0  d5 20 dd e4 68 71 cb 01  60 00 00 00 00 00 00 00  |. ..hq..`.......|
000000b0  5c 00 00 00 00 00 00 00  20 00 00 00 00 00 00 00  |\....... .......|
000000c0  0c 02 4d 00 45 00 4e 00  55 00 53 00 45 00 7e 00  |..M.E.N.U.S.E.~.|
000000d0  31 00 2e 00 58 00 4d 00  4c 00 00 00 00 00 00 00  |1...X.M.L.......|
000000e0  1e 66 00 00 00 00 01 00  78 00 62 00 00 00 00 00  |.f......x.b.....|
000000f0  f3 65 00 00 00 00 01 00  d5 20 dd e4 68 71 cb 01  |.e....... ..hq..|
00000100  00 46 7e 16 62 43 c9 01  d5 20 dd e4 68 71 cb 01  |.F~.bC... ..hq..|
00000110  d5 20 dd e4 68 71 cb 01  98 00 00 00 00 00 00 00  |. ..hq..........|
00000120  95 00 00 00 00 00 00 00  20 00 00 00 00 00 00 00  |........ .......|
00000130  10 01 4d 00 65 00 6e 00  75 00 53 00 68 00 6f 00  |..M.e.n.u.S.h.o.|
00000140  72 00 74 00 63 00 75 00  74 00 2e 00 78 00 6d 00  |r.t.c.u.t...x.m.|
00000150  6c 00 00 00 00 00 00 00  1e 66 00 00 00 00 01 00  |l........f......|
00000160  70 00 5a 00 00 00 00 00  f3 65 00 00 00 00 01 00  |p.Z......e......|
00000170  d5 20 dd e4 68 71 cb 01  00 46 7e 16 62 43 c9 01  |. ..hq...F~.bC..|
00000180  d5 20 dd e4 68 71 cb 01  d5 20 dd e4 68 71 cb 01  |. ..hq... ..hq..|
00000190  98 00 00 00 00 00 00 00  95 00 00 00 00 00 00 00  |................|
000001a0  20 00 00 00 00 00 00 00  0c 02 4d 00 45 00 4e 00  | .........M.E.N.|
000001b0  55 00 53 00 48 00 7e 00  31 00 2e 00 58 00 00 fe  |U.S.H.~.1...X...|
000001c0  ff ff 83 fe ff ff 02 58  63 00 00 30 7c 02 00 fe  |.......Xc..0|...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 50 63 00 00 00  |...........Pc...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Rubi1200 on 2011-03-22
Thanks for the results.

I have to go offline now, but I have asked another forum member to take a look and offer advice.

Please be patient and wait for an answer.

Thanks.

---

### Post by Mikko8 on 2011-03-22
I do not know if this helps but before the last test I run this in the Windows command prompt through the disc```
bootrec.exe /scanos
```Here is what I got:
```
Successfully scanned Windows installations.
Total identified Windows installations: 0
The operation completed successfully
```After all this I reinstalled Grub and run the test. The results I have posted last time are from this test.

---

### Post by drs305 on 2011-03-22
From what I understand, you can currently boot Ubuntu but not Windows.

First, from inside your Ubuntu installation you could try to simplify the W7 entry to:
```
gksu gedit /boot/grub/grub.cfg
```
> menuentry &#8220;Windows 7&#8243; {
set root=(hd0,1)
chainloader +1
}

Don't run udpate-grub, which would remove the change. 
This would only be a test to see if Windows will work. Reboot to see...

If it doesn't, the next is probably to see if Windows will boot on its own. Don't do this if you don't have a bootable Ubuntu LiveCD, as you are going to lose Grub temporarily.

Make the MBR point to sda1's boot files by installing lilo (partially):
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Don't run any other commands and reboot. This will attempt to boot Windows with no interference from Ubuntu. If it doesn't work, you are most likely going to need a Windows repair disk.

To restore grub2, boot the LiveCD, mount your Ubuntu partition, and reinstall Grub2 to the MBR:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Note you do not use the partition number in the second command.
After rebooting, run "sudo update-grub".

---

### Post by Mikko8 on 2011-03-22
> **drs305 said:**
> ..
To restore grub2, boot the LiveCD, mount your Ubuntu partition, and reinstall Grub2 to the MBR:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Note you do not use the partition number in the second command.
After rebooting, run "sudo update-grub".
Just to be sure, should I run the "sudo update-grub" command via Linux installation or via LiveCD?

---

### Post by drs305 on 2011-03-22
> **Mikko8 said:**
> Just to be sure, should I run the "sudo update-grub" command via Linux installation or via LiveCD?

Only run the command after you have booted normally into your regular Ubuntu installation. You wouldn't really be able to update the files if you tried to do it on the LiveCD.

---

### Post by Mikko8 on 2011-03-22
Editing Grub removed the entry when rebooting.
Reboot after lilo was installed did not show anything at all - computer just halted.

I am not sure what is really on sda1 but I am wondering why not to reboot to sda2 partition if that is where the OS is located?

---

### Post by drs305 on 2011-03-22
> **Mikko8 said:**
> Editing Grub removed the entry when rebooting.
Reboot after lilo was installed did not show anything at all - computer just halted.

I am not sure what is really on sda1 but I am wondering why not to reboot to sda2 partition if that is where the OS is located?

The MBR looks for 3 Windows files: /bootmgr /Boot/BCD and /Windows/System32/winload.exe. If you went directly to sda2 it wouldn't see the first two. 

I don't use Windows and don't know if all 3 have to be in the same folder or not. I'm assuming the ones on sda1 would point to winload.exe on sda2.

You'll have to wait for a Windows user to advise you on how to repair Windows.

Forum member *oldfred* has some links that may help you restore Windows (Post 7):
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

---

### Post by Mikko8 on 2011-03-22
Thanks

---

### Post by Ar88rA on 2011-03-22
Hey, I too have installed Ubuntu 10.10 as a dual-boot, and am now unable to boot into Windows 7. Windows came pre-installed on my pc so I do not have a install disk. I'm not sure what is wrong so some help would be nice. (:

---

### Post by oldfred on 2011-03-22
If you do not have a windows repair CD my post #9  in the link drs305 posted has links to a repair CD.

Windows has a separate boot partition that has the  two files - /bootmgr /Boot/BCD and the main install then has /Windows/System32/winload.exe. The boot flag then is set for windows to boot from the first boot partition. Grub finds the first two files & boots windows from that boot partition. 

Win7 can be installed like Vista into one partition and will work from that.  Windows creates the new boot partition so you can encrypt the main install if desired since you cannot encrypt the boot files. Also future version using efi will need a separate boot partition & this is to get users used to it.

The boot script shows the files as ok, but sometimes the internal structure is messed up. Windows repairs should fix it. Sometimes you have to move boot flag and repair the main install, but that usually also adds the first two files to the main install and in effect obsoletes the windows boot partition.

---

### Post by engaso on 2011-11-11
Hello :) 

I  some how solved a similar problem, by using fdisk framework the Linux .
Step1: sudo fdisk -l
It will show you the different partitions. For me that what I get now(After it's fixed)

***/dev/sda1   *           1         154     1228800    7  HPFS/NTFS***
 ***Partition 1 does not end on cylinder boundary.***
 ***/dev/sda2             154       18224   145149948    7  HPFS/NTFS***
 ***Partition 2 does not end on cylinder boundary.***
 ***/dev/sda3           18224       29127    87576577    f  W95 Ext'd (LBA)***
 ***Partition 3 does not end on cylinder boundary.***
 ***/dev/sda4           29127       30402    10240000    7  HPFS/NTFS***
 ***Partition 4 does not end on cylinder boundary.***
 ***/dev/sda5           18224       25211    56122368    7  HPFS/NTFS***
 ***/dev/sda6           25211       29127    31453184   83  Linux***

Look at the sizes of the partitions, make sure which ones are the ones you want to bring them back

Step2: sudo fdisk /dev/sda

Step3: Hit m to see the list of functions
*** a   toggle a bootable flag***
 ***   b   edit bsd disklabel***
 ***   c   toggle the dos compatibility flag***
 ***   d   delete a partition***
 ***   l   list known partition types***
 ***   m   print this menu***
 ***   n   add a new partition***
 ***   o   create a new empty DOS partition table***
 ***   p   print the partition table***
 ***   q   quit without saving changes***
 ***   s   create a new empty Sun disklabel***
 ***   t   change a partition's system id***
 ***   u   change display/entry units***
 ***   v   verify the partition table***
 ***   w   write table to disk and exit***
 ***   x   extra functionality (experts only)***

Step4: Hit c to toggle the dos compatibility flag (Which is very important)
Step5 : Hit l to list known partition types
Step6: Hit t to 
It would show you this:

***Partition number (1-6): ***

Step7: choose the number of partition that windows on it, from step 1.
Step8: choose 7 for ( **7  HPFS/NTFS** )

Step9: Reboot and hope you can access your Windows again!

---

