---
title: "Computer cannot boot - help with Grub!"
date: 2011-02-19
forum: General Help
---

### Post by CrimsonRaccoon on 2011-02-19
Hi everyone, I've been using Ubuntu Netbook edition on my Asus eee pc 1005HA, dual-booting with Windows 7. Things have been fine with it for a month or two. However, I've now run into some trouble with Grub2 and the MBR, and I cannot get my computer to boot into ANY operating system. Right now I'm booting from the Ubuntu installation CD to "try Ubuntu" -- it's the only way I can use my computer at all.

Anyone who could help me would be greatly appreciated! I have looked through the forums and googled, and already tried several methods of fixing Grub2, none of which have worked so far. Here's the situation: I wanted to disable / uninstall Grub2, so that the computer would boot as normal into Windows 7, to fix some problems and then reinstall Grub2 later. To do this I just went to the Windows System Repair environment, opened the command prompt, and entered the two commands "bootrec /fixmbr" and "bootrec /fixboot" with the understanding that this would reset the Windows control of booting, and remove Grub2's control. The result was that my computer cannot boot properly at all. No Windows and no Grub2.

So far I've tried to fix this by using the Super Grub Disk to try to use the auto-repair feature, which failed. I've also tried in various ways to reinstall / repair / update Grub by using the Terminal in Ubuntu (through the "try Ubuntu" CD), but so far none of the methods I've found have worked. 

If anyone could explain or direct me to a step-by-step of how to repair the MBR and install Grub2 from scratch, it would be an enourmous help to me! I'm pretty desperate here.

Here are the resources available to me:
Super Grub Disk
Windows System Repair Disk
Ubuntu Installation Disk

---

### Post by wilee-nilee on 2011-02-19
It sounds like you have the W7 issues fixed, if so here is the reload grub2 from the live cd; three commands, one=fdisk to identify the Ubuntu install partition, and two to mount that and load the mbr.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Any more problems use the bootscript in my signature, feel free to post it in code tags if needed.

---

### Post by CrimsonRaccoon on 2011-02-19
Great, that got Grub2 back and working just as before. Thank you!

So, if I want to remove Grub and restore my computer's boot process to the way it would be if Windows was the only OS, what would be the correct way to do that?

The reason I ask is because I'm trying to troubleshoot Windows start-up issues, and when I run Windows Startup Repair, it results in the error "Boot sector for system disk partition is corrupt." I assume this is because it doesn't recognize Grub2's control and sees it as a problem. So to remove that hurtle, I'd like to be able to temporarily remove Grub and run startup repair without it.

I checked the guide, but it looks like the only uninstallation instructions it has are for going from Grub2 back to Grub Legacy.

---

### Post by wilee-nilee on 2011-02-20
> **CrimsonRaccoon said:**
> Great, that got Grub2 back and working just as before. Thank you!

So, if I want to remove Grub and restore my computer's boot process to the way it would be if Windows was the only OS, what would be the correct way to do that?

The reason I ask is because I'm trying to troubleshoot Windows start-up issues, and when I run Windows Startup Repair, it results in the error "Boot sector for system disk partition is corrupt." I assume this is because it doesn't recognize Grub2's control and sees it as a problem. So to remove that hurtle, I'd like to be able to temporarily remove Grub and run startup repair without it.

I checked the guide, but it looks like the only uninstallation instructions it has are for going from Grub2 back to Grub Legacy.

The guide defaults on reinstalling the grub2 bootloader to the mbr.

To just reload the the win bootloader to the mbr you run from the W7 booted recovery or install disc command line 
bootrec.exe /fixmbr

Here is the command set that the autorepair does basically, personally I would not use it but the commands. Notice the W7 forum link last for a visual to the command line.
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by CrimsonRaccoon on 2011-02-21
Thanks again for the help. But it looks like I have some other problem with the MBR, because following those instructions resulted in the same problem as before: not being able to boot anything at all. Here's what happened with each command line:

*BootRec.exe /fixmbr*
This worked fine.

*chkdsk /r*
This failed. The response was: "Cannot lock current drive. Windows cannot run disk checking on this volume because it is write protected."

*BootRec.exe /FixBoot*
This also failed. The response was: "Element not found."
[I]
BootRec.exe /ScanOs[/I]
This seems to have worked fine; it found the Windows OS on drive C:
[I]
BootRec.exe /RebuiltBcd
[/I]Failed. First, it again found C:/Windows, and asked if I wanted it to add the OS. I typed "Y" for yes (the other options being N: No and A: All), and the result was the message "Element not found."

After exiting the command prompt and rebooting, my computer just gives a black screen with the white text: 
"Reboot and select proper Boot device or insert boot media in selected boot device and press a key."

So I can't get into any operating system without using Super Grub Disk. Presently I'm going to reinstall Grub2 again following the instructions in the guide you gave me earlier. But is there anything I can do to solve these issues I'm having?

---

### Post by wilee-nilee on 2011-02-21
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Did the chkdsk give you an option to run on reboot?

---

### Post by CrimsonRaccoon on 2011-02-21
Alright, here's the code from running the script in the Ubuntu installation disc OS. As for the chkdsk, no, it didn't give me any options to do anything.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Vista: Fat 32
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   167,775,974   167,773,927   7 HPFS/NTFS
/dev/sda2         167,782,860   467,388,415   299,605,556   f W95 Ext d (LBA)
/dev/sda5         167,782,923   428,325,029   260,542,107   7 HPFS/NTFS
/dev/sda6         428,326,912   465,668,095    37,341,184  83 Linux
/dev/sda7         465,670,144   467,388,415     1,718,272  82 Linux swap / Solaris
/dev/sda3         467,388,416   488,359,935    20,971,520   b W95 FAT32
/dev/sda4         488,359,936   488,392,064        32,129   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F8126B77126B3A30                       ntfs       Windows                       
/dev/sda2: PTTYPE="dos" 
/dev/sda3        066C-CC6C                              vfat       FACTORY RES                   
/dev/sda5        C4246EAF246EA3E0                       ntfs       Media                         
/dev/sda6        7d7db03b-8c4d-4be3-bbad-a73ab50f8905   ext4       Ubuntu                        
/dev/sda7        efcae654-6144-4da8-955b-0337ac0da091   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Media             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="8"
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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 7d7db03b-8c4d-4be3-bbad-a73ab50f8905
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 7d7db03b-8c4d-4be3-bbad-a73ab50f8905
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 7d7db03b-8c4d-4be3-bbad-a73ab50f8905
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=7d7db03b-8c4d-4be3-bbad-a73ab50f8905 ro  quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 7d7db03b-8c4d-4be3-bbad-a73ab50f8905
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=7d7db03b-8c4d-4be3-bbad-a73ab50f8905 ro single  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 7d7db03b-8c4d-4be3-bbad-a73ab50f8905
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=7d7db03b-8c4d-4be3-bbad-a73ab50f8905 ro  quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 7d7db03b-8c4d-4be3-bbad-a73ab50f8905
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=7d7db03b-8c4d-4be3-bbad-a73ab50f8905 ro single  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 7d7db03b-8c4d-4be3-bbad-a73ab50f8905
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7d7db03b-8c4d-4be3-bbad-a73ab50f8905 ro  quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 7d7db03b-8c4d-4be3-bbad-a73ab50f8905
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7d7db03b-8c4d-4be3-bbad-a73ab50f8905 ro single  quiet
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 7d7db03b-8c4d-4be3-bbad-a73ab50f8905
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 7d7db03b-8c4d-4be3-bbad-a73ab50f8905
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f8126b77126b3a30
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 066c-cc6c
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7d7db03b-8c4d-4be3-bbad-a73ab50f8905 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=efcae654-6144-4da8-955b-0337ac0da091 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 226.1GB: boot/grub/core.img
 234.5GB: boot/grub/grub.cfg
 220.7GB: boot/initrd.img-2.6.35-22-generic
 220.7GB: boot/initrd.img-2.6.35-24-generic
 231.2GB: boot/initrd.img-2.6.35-25-generic
 226.2GB: boot/vmlinuz-2.6.35-22-generic
 226.2GB: boot/vmlinuz-2.6.35-24-generic
 226.2GB: boot/vmlinuz-2.6.35-25-generic
 231.2GB: initrd.img
 220.7GB: initrd.img.old
 226.2GB: vmlinuz
 226.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  06 7e 7a 61 72 a2 48 63  34 5a 45 5b 5f 57 b3 fc  |.~zar.Hc4ZE[_W..|
00000010  97 83 30 b5 8d 2f ec 52  a3 51 96 b6 66 a9 84 8b  |..0../.R.Q..f...|
00000020  39 f4 c0 ed c2 1e 07 1f  a7 6c ec 38 ed b5 e1 d8  |9........l.8....|
00000030  ab 85 45 d1 97 61 7a d3  7c db ed 2e ed e5 2b 75  |..E..az.|.....+u|
00000040  b8 e1 ed 2b 88 dd 2f 7b  6d ca 3e e2 70 a7 c1 e8  |...+../{m.>.p...|
00000050  20 af d5 ca 1f 82 09 20  bc 65 84 9e 7c 69 12 c3  | ...... .e..|i..|
00000060  a6 9d 21 7a e1 3a e4 d2  ac d2 61 b3 12 94 79 90  |..!z.:....a...y.|
00000070  13 59 f7 05 4b f0 b0 99  84 46 7c 6c 34 94 5b d9  |.Y..K....F|l4.[.|
00000080  22 8d 7f 39 e9 92 46 87  84 e8 74 10 ec d4 21 2c  |"..9..F...t...!,|
00000090  9f e5 d4 e2 39 11 92 a1  ed e3 f6 ee 3a c3 2b 13  |....9.......:.+.|
000000a0  4f 10 21 c7 c1 4e 76 f6  0c 67 98 52 1e d1 df 1a  |O.!..Nv..g.R....|
000000b0  ee b5 8a bf 07 3e d3 94  1f 9c 0a 89 a3 60 9f cf  |.....>.......`..|
000000c0  43 85 2f 8b 8e c7 8e 86  6b b1 ee e2 ca e0 d0 bf  |C./.....k.......|
000000d0  19 2d 33 fd d8 d9 8d d6  39 d1 e1 a0 98 c0 d9 75  |.-3.....9......u|
000000e0  2c 50 c2 dd 6a 63 b2 93  c3 28 90 16 12 69 16 78  |,P..jc...(...i.x|
000000f0  40 a3 f8 fc cb 46 e4 c5  54 e0 98 90 3c 46 f4 5e  |@....F..T...<F.^|
00000100  1f d0 fd 23 7c 7b 03 7b  2e 27 a4 57 15 c7 cf ab  |...#|{.{.'.W....|
00000110  86 7e f3 1e fd e6 f5 c3  96 2d 4f b8 a3 55 12 ea  |.~.......-O..U..|
00000120  3e 5d ff bb dc 72 a3 a4  d0 15 45 01 f0 5c 1c b0  |>]...r....E..\..|
00000130  09 1c 48 bf 93 10 e4 2b  20 13 25 7b f7 4a 52 7f  |..H....+ .%{.JR.|
00000140  ac 63 ed 01 af aa a8 66  c7 4d 98 72 c3 8d 1a eb  |.c.....f.M.r....|
00000150  ec df 11 45 ab 2b cf 63  0f f2 3c 36 53 8a d8 77  |...E.+.c..<6S..w|
00000160  8a 3b df 59 12 7e 3c 26  34 2f ba 0f b0 b2 f0 ba  |.;.Y.~<&4/......|
00000170  4c 24 74 07 65 94 d5 c4  81 2e b3 4c da 6f c4 36  |L$t.e......L.o.6|
00000180  f3 42 f8 23 29 54 7f 47  35 1f cb 35 d7 2f b9 7e  |.B.#)T.G5..5./.~|
00000190  4b 4b 8f 71 e1 ac 17 b7  99 27 a5 18 ad 59 32 19  |KK.q.....'...Y2.|
000001a0  0d e1 5c bd 12 88 89 24  ee 77 ea 44 57 5f 92 97  |..\....$.w.DW_..|
000001b0  05 b6 82 d8 3e d6 b3 97  7b 3a 3b 00 e7 ad 00 fe  |....>...{:;.....|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 9b 8e 87 0f 00 fe  |......?.........|
000001d0  ff ff 05 fe ff ff 32 96  87 0f 02 c8 39 02 00 00  |......2.....9...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```Another strange thing that has come out of this, is that Windows is now detecting an additional drive partition that it never did before. The newly appeared drive is designated "E," (C is Windows and D is my personal files) but it cannot be accessed without formatting it. I think it was a hidden partition that Asus sets up to store bios files, or something like that. It's only 16 MB. What's strange is that my partition manager, MiniTool Partition Wizard Home Edition v5.2, cannot set the drive to be hidden again. I wonder what could have caused this to happen... v_v

I really appreciate the help! :D

---

### Post by wilee-nilee on 2011-02-21
So whats the problem here the script looks okay. If your trying to just understand MS you might try the W7 forums as well.:)

Actually your missing the bootflag on sda1 the MS C, put it there with gparted, then sda1 will be active. sda3 is the restore it has the boot mgr on it as well, sda4 is the firmware or something, this one is very small.

---

### Post by CrimsonRaccoon on 2011-02-22
Well, the problem is that Grub has done something to my MBR, so that when I remove Grub, my computer is totally unable to boot. Something's happened with Grub that's made Windows incapable of restoring the mbr and boot process. Grub's installed right now, so that's why the boot process looks fine. Should I run the boot script again and post it here after uninstalling Grub?

---

### Post by Quackers on 2011-02-22
How are you trying to remove grub from the mbr? I'm not sure it's even possible without writing zeros to the mbr.
Why are you trying to remove grub from the mbr?
When you install grub to the mbr of the drive it overwrites the mbr. Consequently if you remove grub, there's nothing left in the mbr to boot anything!  Why would you expect anything else?

---

### Post by CrimsonRaccoon on 2011-02-22
Well, for the how am I trying to remove it, I'm following wilee-nilee's instructions on removing Grub and restoring the Windows bootloader.

Going into the Windows recovery environment, entering these commands into a command prompt should result in Grub being cleanly removed and restore my comptuer's boot process to the way it was when purchased:

[I]BootRec.exe /fixmbr
chkdsk /r
BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd[/I]

The problem is, it appears the process of installing Ubuntu or Grub has done something to the boot process that Windows can't restore. Entering these commands into the command prompt results in a few error messages, which shouldn't happen according to the various guides on Grub.

---

### Post by Quackers on 2011-02-22
By running /fixmbr you are over-writing grub in the mbr of the drive, which makes only Windows bootable.
chkdsk probably isn't still required.
/fixboot repairs a part of the mbr (probably not needed now)
/scanos scans the hard drive for operating systems (not needed any more)
/rebuildbcd, surprisingly enough rebuilds the /boot/BCD file (not needed now).

You certainly don't need to run all of those commands every time.

When you re-install grub to the mbr it over-writes the Windows entry in the mbr. 

Is all this being done to try and get the Windows recovery console to run? Don't you have a key to press at boot for that purpose?

---

### Post by CrimsonRaccoon on 2011-02-22
This is being done for the purpose of getting my computer to boot as normal into Windows, without using Grub at all. Basically I'd like to be capable of getting my computer set up the way it was when purchased. No Grub, just Windows.

The problem is that running these commands in the prompt results in totally destroying my computer's ability to boot. Grub is removed, but when I boot my computer, I get a black screen asking to insert selected boot media. I then can't do anything with my computer except boot from a CD or USB drive.

---

### Post by Quackers on 2011-02-22
So you want to forget about Ubuntu, yes? Just have Windows on your pc? Well, you've been there already haven't you, when you ran /fixmbr and Windows booted.
I don't understand.

---

### Post by CrimsonRaccoon on 2011-02-22
Yes, you definitely don't understand, lol. I say running those commands results in my computer being unable to boot. What this means is that running /fixmbr does NOT result in Windows booting. It results in my computer completely failing to boot. It doesn't start anything. I can't run Windows without Grub, and I'd like to be able to. That's the goal. =)

---

### Post by Quackers on 2011-02-22
Ah, I understand now.
You obviously missed a bit of Wilee-Nilee's post telling you to put a boot flag on sda1.
Ok, boot from the Windows repair/installation disc and enter the recovery console. When it arrives select the Command Prompt option and then enter these commands, one at a time pressing enter after each line.
```
diskpart
select disk 0
select partition 1
active
exit
bootrec.exe /fixmbr
```

Please note! the 0 in the second line is a nought, not an O and
in the last line there is a space between bootrec.exe and /fixmbr

If all runs ok please reboot and see if Windows then boots ok.

---

### Post by CrimsonRaccoon on 2011-02-22
Yup, that did it. Thanks a lot! I certainly would not have figured that out on my own.

---

### Post by Quackers on 2011-02-22
Aha! Excellent  :-)
You're welcome.

---

### Post by CrimsonRaccoon on 2011-02-22
The reason I wanted to remove Grub and restore the Windows booting process, is because a few weeks after first installing Grub and Ubuntu, Windows spontaneously lost the ability to go into hibernate mode. In trying to figure out why, it seemed like it had something to do with the boot process, so I wanted to remove Grub to see if that would get it working again. That's when I ran into the problems that brought me to this forum.

I'm surprised and happy to see that, after running those commands you gave, not only is Windows booting properly, but hibernation is also working perfectly fine again!

If the problem came down to the boot flag being on the wrong partition, is it normal for Grub to move the boot flag, or is it possible to keep it in partition 1 so Windows can recognize it? I'd like to keep Ubuntu on my computer as a back-up OS, but I'd also like to keep the ability to hibernate in Windows.

---

### Post by Quackers on 2011-02-22
No, it is not likely that grub removed the boot flag. That usually only happens with a user input of some kind, but not sure what.
The hibernation problem may be caused by several things, but I assume the chkdsk that wilee-nilee suggested may have fixed that. It may be that the hibernation problem was caused by improper shrinking of the Windows partition, but I'm not sure. You're partition table is not exactly normal.
The boot flag is only used by Windows (and sometimes by your pc's bios). It is an irrelevance to Linux.

---

