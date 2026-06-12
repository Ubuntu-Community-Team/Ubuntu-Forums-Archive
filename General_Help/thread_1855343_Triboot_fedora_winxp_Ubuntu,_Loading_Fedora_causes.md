---
title: "Triboot fedora winxp Ubuntu, Loading Fedora causes Ubuntu to reset after login"
date: 2011-10-06
forum: General Help
---

### Post by zaptree on 2011-10-06
Hi, I'm having a peculiar problem with my triple boot setup.  I have WinXP, Fedora 15 and Ubuntu 10.04 installed on one hard disk.

 Every time I boot Fedora 15 if I reset and try to boot into Ubuntu my computer resets by itself right after I log in, when it re-boots login works fine. Same thing happens with WinXP, if I log in into Fedora and reset and load Windows it also resets after login. If I go from WinXP reset and then Ubuntu or vice versa everything is fine. 

I think the problem started after installing Ubuntu although I'm not sure of that since I did it a day after Fedora. I was thinking this might be something to do with the bootloader from Ubuntu having some conflict with Fedora ( I dont even know if that is possible). I'm a total noob so if anyone knows to point me to the right direction I'd appreciate it.

My installation setup looks like this:

Primary Partition - Windows XP
Extended Partition
--Swap
--/ Fedora 15
--/ Ubuntu 10.04

I installed Ubuntu last and so I'm using its bootloader GRUB 2.

Thanx

---

### Post by amjjawad on 2011-10-06
> **zaptree said:**
> Hi, I'm having a peculiar problem with my triple boot setup.  I have WinXP, Fedora 15 and Ubuntu 10.04 installed on one hard disk.

 Every time I boot Fedora 15 if I reset and try to boot into Ubuntu my computer resets by itself right after I log in, when it re-boots login works fine. Same thing happens with WinXP, if I log in into Fedora and reset and load Windows it also resets after login. If I go from WinXP reset and then Ubuntu or vice versa everything is fine. 

I think the problem started after installing Ubuntu although I'm not sure of that since I did it a day after Fedora. I was thinking this might be something to do with the bootloader from Ubuntu having some conflict with Fedora ( I dont even know if that is possible). I'm a total noob so if anyone knows to point me to the right direction I'd appreciate it.

My installation setup looks like this:

Primary Partition - Windows XP
Extended Partition
--Swap
--/ Fedora 15
--/ Ubuntu 10.04

I installed Ubuntu last and so I'm using its bootloader GRUB 2.

Thanx

Hello and Welcome :)

After installing Ubuntu, where did you install GRUB2? to MBR (sda)?
Fedora 15 uses GRUB Legacy (Fedora 16 will have GRUB2-FINALLY!) while as you know Ubuntu 10.04 is using GRUB2.

---

### Post by garvinrick4 on 2011-10-06
Welcome to the Ubuntu-Forums:
Fedora uses grub-legacy (grub) and Ubuntu uses Grub2 (grub-pc) they do not play well
together. If you want someone to analyze your boot problems run this script and post.
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 
Lets say you download it to Desktop and extract it by right clicking and using "archive manager" 
then run this code and will put a RESULTS file on Desktop copy and paste
here. After pasting highlight whole thing (rather large) and hit the # sign in upper right
or message box will put in nice code box to read in.
```
sudo bash ~/Desktop/boot_info_script.sh
```

---

### Post by zaptree on 2011-10-06
Hi guys and thanks for the super quick reply, I guess this forum never sleeps :)
Yes I do believe that GRUB 2 is installed on the mbr of sda (confirmed by the script I just ran). I did read before that the GRUB 2 doesn't play well with GRUB-legacy, but I assumed that when I installed Ubuntu and thus GRUB 2 it overwrote the Fedora GRUB-legacy so there would be no problems.

Another thing I'm a bit confused about is does grub play any role on the system after it has started to boot an operating system? My computer resets right after I login from the GUI so I would think that GRUB's job has been over from the moment the OS started to load.

Also another thing I noticed which might be important is that the problem exists only if I chose to reset the system from Fedora as opposed to shutting down. So if I load Fedora then select reset from the power off options and after reset choose Ubuntu(or winXP) in the GRUB menu, after loading when I login to the OS the system will reset and then work fine after loading again. If I login to Fedora and select shut down instead of reset and then re open my computer and login to Ubuntu (or winXP) everything works fine. So this leads me to think that the problem lies at something that is stored in memory by Fedora which gets flushed only when shutting down. I'm probably totally off here just sharing my novice thoughts:)

Here is the output from the script that you asked me to run:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 9 for /boot/grub.

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

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda5 starts at sector 614401263. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   614,401,199   614,401,137   7 NTFS / exFAT / HPFS
/dev/sda2         614,401,261 1,543,368,703   928,967,443   f W95 Extended (LBA)
/dev/sda5         614,401,263 1,128,299,759   513,898,497   b W95 FAT32
/dev/sda6       1,128,299,823 1,128,904,559       604,737  83 Linux
/dev/sda7       1,128,904,623 1,232,627,759   103,723,137  83 Linux
/dev/sda8       1,232,627,823 1,249,002,719    16,374,897  82 Linux swap / Solaris
/dev/sda9       1,249,003,520 1,543,368,703   294,365,184  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        C8E4C1D4E4C1C542                       ntfs       
/dev/sda5        12E0-0F85                              vfat       DATA 250
/dev/sda6        fde36985-6cf6-401f-8c42-4092c37434f4   ext4       
/dev/sda7        8fc98b22-73e8-48c0-ad82-f80c75b7ecda   ext4       _Fedora-15-i686-
/dev/sda8        1419e814-dee8-48d4-bb3c-a34dae6453de   swap       
/dev/sda9        a299db20-d3de-48a8-a8d4-f82fbab6e9ee   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

============================= sda6/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,5)
#          kernel /vmlinuz-version ro root=/dev/sda7
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=2
timeout=5
splashimage=(hd0,5)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.40.4-5.fc15.i686)
    root (hd0,5)
    kernel /vmlinuz-2.6.40.4-5.fc15.i686 ro root=UUID=8fc98b22-73e8-48c0-ad82-f80c75b7ecda rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.40.4-5.fc15.i686.img
title Fedora (2.6.38.6-26.rc1.fc15.i686)
    root (hd0,5)
    kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=UUID=8fc98b22-73e8-48c0-ad82-f80c75b7ecda rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
title Other
    rootnoverify (hd0,0)
    chainloader +1
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 538.030419827 = 577.705764352  grub/grub.conf                                 2
 538.030419827 = 577.705764352  grub/menu.lst                                  2
 538.028840542 = 577.704068608  grub/stage2                                    1
 538.046089649 = 577.722589696  initramfs-2.6.38.6-26.rc1.fc15.i686.img        2
 538.069862843 = 577.748115968  initramfs-2.6.40.4-5.fc15.i686.img             3
 538.026885509 = 577.701969408  vmlinuz-2.6.38.6-26.rc1.fc15.i686              1
 538.050177097 = 577.726978560  vmlinuz-2.6.40.4-5.fc15.i686                   1

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Mon Oct  3 14:57:22 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=8fc98b22-73e8-48c0-ad82-f80c75b7ecda /                       ext4    defaults        1 1
UUID=fde36985-6cf6-401f-8c42-4092c37434f4 /boot                   ext4    defaults        1 2
UUID=1419e814-dee8-48d4-bb3c-a34dae6453de swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=========================== sda9/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set a299db20-d3de-48a8-a8d4-f82fbab6e9ee
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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set a299db20-d3de-48a8-a8d4-f82fbab6e9ee
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
menuentry 'Ubuntu, with Linux 2.6.32-34-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set a299db20-d3de-48a8-a8d4-f82fbab6e9ee
    linux    /boot/vmlinuz-2.6.32-34-generic-pae root=UUID=a299db20-d3de-48a8-a8d4-f82fbab6e9ee ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-34-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set a299db20-d3de-48a8-a8d4-f82fbab6e9ee
    echo    'Loading Linux 2.6.32-34-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-34-generic-pae root=UUID=a299db20-d3de-48a8-a8d4-f82fbab6e9ee ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-34-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set a299db20-d3de-48a8-a8d4-f82fbab6e9ee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set a299db20-d3de-48a8-a8d4-f82fbab6e9ee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set C8E4C1D4E4C1C542
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Fedora (2.6.40.4-5.fc15.i686) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set fde36985-6cf6-401f-8c42-4092c37434f4
    linux /vmlinuz-2.6.40.4-5.fc15.i686 ro root=UUID=8fc98b22-73e8-48c0-ad82-f80c75b7ecda rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.40.4-5.fc15.i686.img
}
menuentry "Fedora (2.6.38.6-26.rc1.fc15.i686) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set fde36985-6cf6-401f-8c42-4092c37434f4
    linux /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=UUID=8fc98b22-73e8-48c0-ad82-f80c75b7ecda rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=a299db20-d3de-48a8-a8d4-f82fbab6e9ee /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=1419e814-dee8-48d4-bb3c-a34dae6453de none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 687.706371307 = 738.419093504  boot/grub/core.img                             1
 679.766357422 = 729.893568512  boot/grub/grub.cfg                             1
 687.836097717 = 738.558386176  boot/initrd.img-2.6.32-34-generic-pae          1
 687.702629089 = 738.415075328  boot/vmlinuz-2.6.32-34-generic-pae             1
 687.836097717 = 738.558386176  initrd.img                                     1
 687.702629089 = 738.415075328  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  f2 ab fe 05 be 05 b8 12  e3 73 ef 4d 07 64 14 34  |.........s.M.d.4|
00000010  c7 69 7f ef 0d c9 76 42  9a f5 05 b2 76 10 4a 33  |.i....vB....v.J3|
00000020  1a 11 fd bd a4 71 b7 9f  23 ed bb c6 db 7e 47 bf  |.....q..#....~G.|
00000030  7d 15 19 e7 f4 dc 47 db  7e 26 37 d9 a6 55 03 02  |}.....G.~&7..U..|
00000040  a5 53 66 3f dc a4 d6 ae  73 d1 10 c4 71 2f 1a 0f  |.Sf?....s...q/..|
00000050  30 7e af e8 b1 11 c3 06  4b 81 d1 1d 2b 0a b8 c6  |0~......K...+...|
00000060  6e 35 96 de 40 70 4e 30  01 b3 7e 99 8b 59 62 9c  |n5..@pN0..~..Yb.|
00000070  32 26 06 64 1b c0 c3 e1  22 28 00 f5 65 df 0f 5b  |2&.d...."(..e..[|
00000080  54 25 2b e2 35 2c 35 7b  20 c0 fb be f9 ac cd c2  |T%+.5,5{ .......|
00000090  31 38 21 03 04 00 66 47  43 be 51 d3 23 ef 8e 7c  |18!...fGC.Q.#..||
000000a0  d0 97 9f 96 77 23 7e 41  60 a5 49 9b 4c ba b2 b2  |....w#~A`.I.L...|
000000b0  87 b3 e3 be 83 c0 41 4e  0e 05 25 5c 1e 27 fd 7d  |......AN..%\.'.}|
000000c0  03 e0 f1 b0 06 c2 e4 40  c3 57 d7 e7 a3 6d bf 43  |.......@.W...m.C|
000000d0  6d b9 16 1b e1 47 7a ee  36 f3 bc 6d b7 38 db 6f  |m....Gz.6..m.8.o|
000000e0  ba e2 26 e3 df ee db 9f  5b 81 90 27 fa 1e 6f 64  |..&.....[..'..od|
000000f0  3e 3f dc f7 50 db 7b b6  02 ef 6b 62 80 52 17 42  |>?..P.{...kb.R.B|
00000100  e1 19 ad b0 0c a5 81 ff  c0 98 da 0c b0 29 96 3d  |.............).=|
00000110  59 56 d3 12 76 b6 df bd  24 47 4b 76 60 62 70 a4  |YV..v...$GKv`bp.|
00000120  f0 e1 43 5c e0 e2 4c e1  a5 13 87 99 ba 89 ca d4  |..C\..L.........|
00000130  3a f1 81 7c 91 70 28 07  b8 d8 2b 47 c0 df 64 79  |:..|.p(...+G..dy|
00000140  9e 6d 2a 6d 24 cf 5a 09  cd 30 42 a0 c3 dc 4f 2a  |.m*m$.Z..0B...O*|
00000150  46 04 21 09 2d ff 95 09  3e 5d 0e e0 46 8a b3 72  |F.!.-...>]..F..r|
00000160  88 82 76 4f f9 70 85 fc  01 e0 c9 82 1b 59 fc fa  |..vO.p.......Y..|
00000170  51 e8 84 ae 77 e3 e6 b7  36 e7 69 2e ae 22 14 c1  |Q...w...6.i.."..|
00000180  3a 6d 0f 80 f7 db 90 7c  25 00 77 fe 36 69 3b 76  |:m.....|%.w.6i;v|
00000190  c8 0a dd 5b 11 ac b9 a2  62 e3 e6 98 1e 89 1b e1  |...[....b.......|
000001a0  e8 7e da ac b9 5a 61 9f  6c db ed 0e f2 f2 76 73  |.~...Za.l.....vs|
000001b0  b2 b8 60 0a 41 1c 7a de  ef e2 72 f0 3f 9e 00 ef  |..`.A.z...r.?...|
000001c0  ff ff 0b ef ff ff 02 00  00 00 01 78 a1 1e 00 fe  |...........x....|
000001d0  ff ff 05 fe ff ff 03 78  a1 1e 80 3a 09 00 00 00  |.......x...:....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 



```

---

### Post by Bobhuber on 2011-10-06
OK I just ran into almost the same problem on a laptop I was fooling around with right after an install of Ubuntu 11.04
After hours of frustration I ran a virus check in windows (Win 7 in my case)
149 infected files and I have no idea why it was affecting the boot cycle but it was.

---

### Post by garvinrick4 on 2011-10-06
> So this leads me to think that the problem lies at something that is  stored in memory by Fedora which gets flushed only when shutting down.  I'm probably totally off here just sharing my novice thoughts:smile:It is because Fedora and all Redhat cousins if grub is installed will make a /boot paritition
and yours is sda6 where your fedora boot files are held. sda7 is your operating system.

I choose at install to always install Ubuntu first with grub-pc (grub2) and then any installations using grub-legacy (grub) after and not install grub at all in the installation
application (anaconda) and then go into Ubuntu and update-grub as to put Fedora in its config file and as a menu entry to boot from.

Yours is now a working system and we could get rid of the fedora /boot partition sda6 and remove all things grub-legacy (grub) from fedora install sda7. That is up to you, always
a chance of something going amiss no matter how small and you are booting. Would not advise at all.

If you had the time I would clean up my partition table and install Ubuntu first and
fedora second as explained. 

Fedora uses its /boot partition to distribution upgrade from 15 to 16 if /boot is gone
have to fresh install 16 instead of upgrade through RPM's.

Your decision zaptree. I do not know how new you are to Linux and do not want to get you in a situation where you are lost. No what I mean. Oh yes and welcome to the Ubuntu Forums.

Could be a user whom is a Fedora or Redhat cousin user who has a better option, let Thread hang around for a while and see if better options and or post in a Fedora Forum this is a Fedora
and grub-legacy thing that is going on.

---

### Post by zaptree on 2011-10-06
While looking at the output of the script I assumed that sda6 was storing stage2 of the grub2 of Ubuntu, after some reading I realise u can tell by the fact it has menu.lst and grub.conf that its grub-legacy thus its from Fedora.

One thing I dont understand is why this /boot of fedora is affecting my other OSs?

I will re-install since I don't want to have any troubles down the line. So I will just remove fedora and its /boot partitons, re install and run update grub. I'm assuming removing the 2 partitions will mess up the grub because sda8 and sda9 will become sda6 and sda7 so the mbr will point to the wrong partition? So my solution will be to re-install Grub from the Ubuntu live cd?

I'm sorry for the many questions I just like to have a good understanding what is going on. I believe the re-installation will solve my problem so I will do it on the weekend where I'll have more time and post back if everything was ok.

Thanks very  much you have been very helpful!

---

### Post by garvinrick4 on 2011-10-06
If you go into a Live Cd of Ubuntu (install Cd using Try UBuntu) and use "gparted" to make your partition
table and install Fedora into the partition you have made for it without choosing to install grub at install
and going into Ubuntu after Fedora install and
```
sudo update-grub
```all will be fine.
Take a screenshot of gparted and post here and I will help you. Here is a partition link to read.
We will get rid of sda6 and have sda7 take that empty space. Then format and install Fedora in that same spot.
[HowToPartition - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by garvinrick4 on 2011-10-06
> One thing I dont understand is why this /boot of fedora is affecting my other OSs? sda6 the /boot partition will still be apart of the config file for Ubuntu
because it is part of partition table with boot files in it and grub2 picks it up when it
runs the "os-prober" package to pick up other operating systems and put them in
config file and as a menu entry to boot with in grub2.
This package below runs when you run sudo update-grub or sudo grub-mkconfig
```
Package: os-prober                       
State: installed
Automatically installed: no
Version: 1.44ubuntu1
Priority: optional
Section: utils
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 197 k
Depends: libc6 (>= 2.4)
Description: utility to detect other OSes on a set of drives
 This package detects other OSes available on a system and outputs the results
 in a generic machine-readable format.
```Some will install grub in Fedora and its Redhat cousins to same partition but I just
found it so much easier to not install at all and use Ubuntu's grub2 to control the boot process.
Only use Ubuntu's Operating Systems nowadays but did spend some time experimenting with booting 
with mixed grub (grub) and grub2 (grub-pc). Came to previous posts conclusions on best way to install.

---

### Post by zaptree on 2011-10-07
After trying to get this fixed and reinstalling it appears that the problem persist no matter what. Actually the problem happens even when I run the Fedora live cd without even installing and then resetting from inside the live cd. From what I know the Live cd saves nothing at all on disk and only stores data in RAM memory. This makes sense since when I'd shut down the computer and open it again the problem did not occur thus meaning that Fedora stores something on my RAM that messes up the boot process of the other OSs. So this just seems to be some bug of Fedora.

Anyway I think I'm just going to abandon Fedora all together since I use Ubuntu anyway. Fedora was actually for my girlfriend to use since she likes the gnome3 shell, so I'll just look for another distro that has it.

Regardless of my failure I want to thank you garvinrick4 for your help, I definitely learned a few things.

---

### Post by garvinrick4 on 2011-10-07
> Fedora was actually for my girlfriend to use since she likes the gnome3 shell, so I'll just look for another distro that has it.Ubuntu 11.04 Natty with ppa for gnome-shell. Install 11.04 and set up and then. ( I have one install on Natty running this ppa and it runs smooth, real smooth.)
```
sudo add-apt-repository ppa:gnome3-team/gnome3 
``` ```
sudo apt-get update
``` ```
sudo apt-get install gnome-shell
```Here is a list of ppa's for you: 
 Google ppa and read up on them. And look into launchpad.net
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas) 

Here of course is Ubuntu 11.04
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

I cannot explain why Fedora would not install on your machine, I have played
around with plenty of the yum's and they managed fine to install and boot, a mystery.
You enjoy your Ubuntu zaptree and use these Forums.

---

### Post by zaptree on 2011-10-09
Thanx for the info! I will do what you say but I'll wait for a few days and put 11.10 since its almost out! Thanx again for all the help.

---

