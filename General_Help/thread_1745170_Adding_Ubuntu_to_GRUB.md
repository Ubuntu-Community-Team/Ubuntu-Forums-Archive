---
title: "Adding Ubuntu to GRUB"
date: 2011-04-30
forum: General Help
---

### Post by electricmaster on 2011-04-30
Can someone help me? I've got a bit of a problem... I have an Acer One netbook, and I've been working forever to install XP alongside Ubuntu (Natty). Today I pulled out the HD and put it in a laptop with a CD drive and installed it that way. When I did this, it deleted the GRUB bootloader. I reinstalled the GRUB bootloader though the Natty live CD and XP was on the GRUB menu, but Ubuntu wasn't. /boot seems to have been deleted, so I'm missing vmlinuz and everything. I've tried update-grub a thousand times, but Ubuntu doesn't come up. I think it's because of the missing /boot (/boot/grub still exists though, after reinstalling it). I've downloaded vmlinuz and the intrsomething.gz from the Ubuntu website, but it hasn't changed anything. Any ideas on how to add Ubuntu back to the GRUB bootloader?

---

### Post by drs305 on 2011-04-30
electricmaster,

Welcome to the Ubuntu forums.

Grub2 probably isn't going to install properly, nor your system work correctly, until you have installed the kernel. You will have to 'chroot' into your Ubuntu partition to properly install the kernel. You can't just stick the downloaded package into /boot.

You can use the chroot-ing instructions in my signature line ("Chroot") to mount your Ubuntu partition and install the kernel from a Natty LiveCD. Once you get to the "root" prompt (i.e. successfully chrooted), you can install the latest kernel with the following. You don't use 'sudo' in a chroot environment:```

apt-get update
apt-get install linux-image
```
I believe that will get the kernel and initrd images properly installed. Watch the terminal output, as installing a new kernel should run 'update-grub' near the end and generate a new Grub menu.

If you see that, you should be able to boot and get a working Grub menu at boot.

If you have questions just ask before doing something you don't understand.

---

### Post by electricmaster on 2011-04-30
Thank you thank you. Been meaning to sign up for a while, and I figure this is a good a time as any. 

And okay thanks, I'll try that. The way I've been installing GRUB, is it alright btw? I've been mounting my Ubuntu and Windows partiions to /mnt and then doing a mount --bind on the required folders to /mnt/dev etc. Then I chroot'd into /mnt and ran grub-install.

**[COLOR=Red]EDIT:[/COLOR]**
[COLOR=Black]Okay, I ran it, but I'm not sure if it worked correctly. This is what the terminal gave back:
[/COLOR]```

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sda1 /mnt
root@ubuntu:~# apt-get update
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty InRelease
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en
Ign http://archive.ubuntu.com natty InRelease                                  
Ign http://archive.ubuntu.com natty-updates InRelease                          
Get:1 http://archive.ubuntu.com natty Release.gpg [198 B]
Ign http://security.ubuntu.com natty-security InRelease
Get:2 http://archive.ubuntu.com natty-updates Release.gpg [198 B]
Get:3 http://archive.ubuntu.com natty Release [39.8 kB]
Get:4 http://security.ubuntu.com natty-security Release.gpg [198 B]
Get:5 http://security.ubuntu.com natty-security Release [23.2 kB]
Get:6 http://archive.ubuntu.com natty-updates Release [23.2 kB]                
Get:7 http://security.ubuntu.com natty-security/main Sources [2,808 B]
Get:8 http://security.ubuntu.com natty-security/restricted Sources [14 B]      
Get:9 http://security.ubuntu.com natty-security/main i386 Packages [11.0 kB]
Get:10 http://security.ubuntu.com natty-security/restricted i386 Packages [14 B]
Ign http://security.ubuntu.com natty-security/main TranslationIndex  
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Get:11 http://archive.ubuntu.com natty/main Sources [862 kB]          
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Get:12 http://archive.ubuntu.com natty/restricted Sources [4,104 B]   
Get:13 http://archive.ubuntu.com natty/main i386 Packages [1,550 kB]
Get:14 http://archive.ubuntu.com natty/restricted i386 Packages [8,986 B]      
Ign http://archive.ubuntu.com natty/main TranslationIndex                      
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                
Get:15 http://archive.ubuntu.com natty-updates/main Sources [3,561 B]          
Get:16 http://archive.ubuntu.com natty-updates/restricted Sources [14 B]       
Get:17 http://archive.ubuntu.com natty-updates/main i386 Packages [14.6 kB]    
Get:18 http://archive.ubuntu.com natty-updates/restricted i386 Packages [14 B] 
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex              
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://archive.ubuntu.com natty/main Translation-en_US                     
Ign http://archive.ubuntu.com natty/main Translation-en                        
Ign http://archive.ubuntu.com natty/restricted Translation-en_US               
Ign http://archive.ubuntu.com natty/restricted Translation-en                  
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US             
Ign http://archive.ubuntu.com natty-updates/main Translation-en                
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en          
Fetched 2,544 kB in 16s (151 kB/s)                                             
Reading package lists... Done
root@ubuntu:~# chroot /mnt apt-get install linux-image
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vorbis-tools id3v2 libgluezilla gtkpod-data libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-image
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,354 B of archives.
After this operation, 32.8 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main linux-image i386 2.6.38.8.22 [2,354 B]
Fetched 2,354 B in 0s (3,855 B/s)       
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package linux-image.
(Reading database ... 168466 files and directories currently installed.)
Unpacking linux-image (from .../linux-image_2.6.38.8.22_i386.deb) ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image (2.6.38.8.22) ...

```

---

### Post by drs305 on 2011-04-30
> **electricmaster said:**
> =
And okay thanks, I'll try that. The way I've been installing GRUB, is it alright btw? I've been mounting my Ubuntu and Windows partiions to /mnt and then doing a mount --bind on the required folders to /mnt/dev etc. Then I chroot'd into /mnt and ran grub-install.

**[COLOR=Red]EDIT:[/COLOR]**
[COLOR=Black]Okay, I ran it, but I'm not sure if it worked correctly. This is what the terminal gave back:

Installing the kernel didn't work as it appears the chroot wasn't successful. Part of the instructions include mounting /dev, /dev/pts, /proc and /sys. It looks like at least /dev/pts wasn't mounted correctly.

These are all mounted by the "for i in ..." command. Just run all the commands as posted, only changing the partition (sdXY) to the correct Ubuntu partition. It's easiest to cut/paste the commands to prevent typos.

---

### Post by electricmaster on 2011-05-01
Okay. I mounted /dev/sda1 to /mnt/temp and did the chroot command in your sig. I reran update-grub and tried to install linux-image. It was already installed so  I ran update-grub, but all it found is my W7 partition on sda2 (I couldnt get XP to install) so I removed and reinstalled linux-image and ran update-grub again. No go. I checked to be sure but all that was there was the Windows bootloader option. Ubuntu still wasn't in the GRUB menu and /boot is still empty on sda1, aside from /boot/grub

---

### Post by drs305 on 2011-05-01
Do you have a separate /boot partition?

It's time to go to this site and download the boot info script. Please run the script and post the contents of RESULTS.txt. It will give us a pretty good idea of your boot file status:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by electricmaster on 2011-05-01
Okay, this is what I got back.
( /dev/sda being my main HD and /dev/sdb being my flash drive with the Ubuntu Live CD on it)
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   274,982,911   274,980,864  83 Linux
/dev/sda2    *    274,982,912   306,440,191    31,457,280   7 HPFS/NTFS
/dev/sda3         306,442,238   312,580,095     6,137,858   5 Extended
/dev/sda5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4213 MB, 4213178368 bytes
255 heads, 63 sectors/track, 512 cylinders, total 8228864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            128     8,228,863     8,228,736   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        14361068-6d4c-4583-9d51-f1cbc09c9678   ext4                                     
/dev/sda2        6C02DC1F02DBEBD8                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ad63070a-48a3-4e59-b39c-40e1c8dcc9d5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4036-F837                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 14361068-6d4c-4583-9d51-f1cbc09c9678
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 14361068-6d4c-4583-9d51-f1cbc09c9678
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 6C02DC1F02DBEBD8
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
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 109.6GB: boot/grub/core.img
  75.7GB: boot/grub/grub.cfg
 109.6GB: boot/grub/stage2

============================= sda2/grub/grub.cfg: =============================

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
true
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 14361068-6d4c-4583-9d51-f1cbc09c9678
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 6C02DC1F02DBEBD8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu Natty" {
set root=(hd0,0)
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: grub/core.img
    ??GB: grub/grub.cfg
    ??GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ba d6 48 6a ca 7a 60 21  9b c5 fc a4 06 9e 1c df  |..Hj.z`!........|
00000010  35 c6 90 4d ed 4b 05 7d  46 d2 e8 18 65 77 7b 2c  |5..M.K.}F...ew{,|
00000020  aa 25 51 29 09 d8 45 6d  34 41 93 8c 52 46 74 a8  |.%Q)..Em4A..RFt.|
00000030  b3 9f 00 61 67 e1 2c 1b  60 8a 14 cb 91 ea fd 82  |...ag.,.`.......|
00000040  b3 eb bd e7 f8 a6 dc 12  a8 c6 b0 07 05 b3 62 b3  |..............b.|
00000050  b8 28 88 ea 86 41 70 a7  95 b3 b6 bc d5 4a 92 da  |.(...Ap......J..|
00000060  54 b9 bc 0c a4 79 84 28  0d ef f6 f1 b8 91 d4 79  |T....y.(.......y|
00000070  ff e2 90 53 47 37 39 d5  cf ad 94 f7 3a 18 7b 48  |...SG79.....:.{H|
00000080  73 00 99 21 83 f1 cb 69  a4 87 f4 c8 c2 ce 1f e1  |s..!...i........|
00000090  3c 11 68 ec a7 73 63 ad  71 e9 b4 b8 ad 99 ba 3e  |<.h..sc.q......>|
000000a0  b5 a1 94 62 e6 7e 82 e4  e7 bf e5 aa 4f 19 8a d2  |...b.~......O...|
000000b0  65 23 67 63 d8 67 04 eb  c7 7d ab 19 e7 76 eb 9f  |e#gc.g...}...v..|
000000c0  6f 5d df 95 e5 4c 06 3d  fe 31 88 bf d7 c2 69 f7  |o]...L.=.1....i.|
000000d0  f6 8a 8e 82 e9 8e 83 1f  f6 e8 aa 58 2e 7d 11 fe  |...........X.}..|
000000e0  aa 3a 19 d0 57 0c fc e4  d0 6e a3 7c 5d d6 5f 81  |.:..W....n.|]._.|
000000f0  7c d9 58 07 47 94 62 2b  5f 6d 2f a8 f9 0b 09 29  ||.X.G.b+_m/....)|
00000100  16 39 d2 01 6b 94 39 eb  1b 49 39 13 37 25 c7 8e  |.9..k.9..I9.7%..|
00000110  d3 12 8d 79 b1 3c 8d 10  98 9c 13 fd cf 07 c5 f4  |...y.<..........|
00000120  14 20 f9 22 07 36 58 83  b6 d1 13 58 6b 20 06 96  |. .".6X....Xk ..|
00000130  90 cd 1d 62 19 6c 30 76  75 e7 bf a5 5f 4f 1c 36  |...b.l0vu..._O.6|
00000140  8c bd 60 ab c8 f4 0f 15  ef 34 47 00 72 2a f7 a7  |..`......4G.r*..|
00000150  da a5 a3 d3 c8 49 f1 d7  ba e6 bd 52 51 96 a0 a5  |.....I.....RQ...|
00000160  4d bd 8f 54 d4 61 f6 ed  2b 59 f8 3b da ef 41 c5  |M..T.a..+Y.;..A.|
00000170  e2 71 05 12 92 70 b0 7f  33 12 d1 23 6e a8 5e ba  |.q...p..3..#n.^.|
00000180  bd bf 26 19 d3 36 5e 9d  f2 c6 46 c3 96 43 b1 37  |..&..6^...F..C.7|
00000190  0e b3 02 ff 70 be e5 49  77 f7 7d 5b 47 da a4 a7  |....p..Iw.}[G...|
000001a0  fd 54 10 8c 24 0c c8 0f  72 bf 5c 04 1d 6d af b6  |.T..$...r.\..m..|
000001b0  e4 3c de 69 21 ad 0b 11  8c 66 29 1d 3a 6d 00 fe  |.<.i!....f).:m..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 58 01  |.X.SYSLINUX...X.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 00 00 00  |........?.......|
00000020  80 8f 7d 00 54 1f 00 00  00 00 00 00 02 00 00 00  |..}.T...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 37 f8 36 40 4e  4f 20 4e 41 4d 45 20 20  |..)7.6@NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 08  40 00 00 66 ba 00 00 00  |..E}.f..@..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```And no, I don't have a separate /boot partition.

---

### Post by drs305 on 2011-05-01
There still isn't a kernel in /boot, according to Grub 2. Let me put all the commands in one place. 

Boot the 11.04 LiveCD and open a terminal, then:

```
sudo mkdir /mnt/temp   
sudo mount /dev/sda1 /mnt/temp  # Mount the main Ubuntu partition. 
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
sudo chroot /mnt/temp
```

At this point, you should be at a root prompt. Sudo is no longer needed. First we will try to install the kernel, then remove Grub2 and install it again. Since you have portions of Grub legacy, we will remove that as well.

```
apt-get update
apt-get install linux-image
ls /boot
```
The second command should install the latest Natty kernel and build an initrd image. Watch the terminal commands, then check the contents of /boot to see if vmlinuz-2.6.38... kernel and initrd.img-2.6.38-... files exist.

Next, remove Grub, and Grub2. It may say that 'grub' (grub legacy) is not installed. You will be warned that you will be left without a bootloader. TAB to OK.```

apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc
update-grub
```
If you don't use kernel options (You'd know what to add if you do), TAB to OK. When it asks where to install, TAB to "sda" and press the SPACE bar to select ONLY "sda". Do not select "sda1". TAB to OK and ENTER.

After it installs, you are done with chroot, so exit, unmount, and reboot.

```
exit
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
sudo umount /dev/sda1

```

---

### Post by electricmaster on 2011-05-01
I have a problem. When I install linux-image, it says it's already installed.

```

root@ubuntu:/# apt-get install linux-image
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image is already the newest version.
The following packages were automatically installed and are no longer required:
  vorbis-tools id3v2 libgluezilla gtkpod-data libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I tried purging and reinstalling and it installed correctly, but /boot still just contains /boot/grub. Everything before that point ran smoothly.

---

### Post by electricmaster on 2011-05-02
Hm. I was working with W7 and I was going into my Ubuntu partition to see if I could find a way to decrypt my home directory from Windows (highly unlikely ik) and I noticed that my root directory had initrd.img, initrd.img.old, vmlinuz, and vmlinuz.old. Do you think that those could be from linux-image?

---

### Post by drs305 on 2011-05-02
> **electricmaster said:**
> Hm. I was working with W7 and I was going into my Ubuntu partition to see if I could find a way to decrypt my home directory from Windows (highly unlikely ik) and I noticed that my root directory had initrd.img, initrd.img.old, vmlinuz, and vmlinuz.old. Do you think that those could be from linux-image?

These are links to the actual kernels and initrd.img files in /boot.  Having these files doesn't prove that the actual files they link to exist, but they should if the files exist in /boot.

One of the things they are useful for is that 'vmlinuz' will always point to the most recent kernel, and initrd.img to the most recent image. When building a custom menu, you can point to 'vmlinuz' and 'initrd.img' in / rather than the specific kernel (with all the identifiers, such as -2.6.38-8) in /boot. That means your custom menu will continue to work even when the kernel version changes.

---

### Post by electricmaster on 2011-05-02
Oh I see. now that you mention it, that would explain why Windows is reading the files as 0KB. So do you have any idea on how to restore the files since Linux-image isnt working?

---

### Post by drs305 on 2011-05-02
> **electricmaster said:**
> Oh I see. now that you mention it, that would explain why Windows is reading the files as 0KB. So do you have any idea on how to restore the files since Linux-image isnt working?

 I was hoping someone might be able to shed some light on what is happening with your system.

This issue still puzzles me. I've thought about it and the only thing I've come up with is trying to install the specific kernel. You might even try installing an earlier one since "linux-image" would be the same as installing the latest one.

You would go through the same chroot process, but try installing a specific kernel, such as:
```
apt-get install linux-image-2.6.38-7-generic 
```
The current kernel is linux-image-2.6.38-7-generic, if you want to try to install that one.

---

### Post by electricmaster on 2011-05-03
Okay. The package you gave me didn't work, but I tried a purge and reinstall with linux-image and it worked, but I had another problem now. 

When Ubuntu starts, it goes to the login screen and I can enter my pass. After I do, it shows the defang background and a dialog pops up that says "Could not update ICEauthority file /home/maclm01/.ICEauthority". Then I get one that says "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)". Then I get that says "Nautilus could not recreate the following home folders: Desktop, .nautilus." Then I get the first time run ecryptfs record your passphrase box. Could the fact that I mounted and unencrypted my home directory from the Live CD have anything to do with it? I ran chown maclm01 -R /home/maclm01 from the Live CD to see if that would fix it but it didn't change anything.

---

### Post by drs305 on 2011-05-03
> **electricmaster said:**
> Okay. The package you gave me didn't work, but I tried a purge and reinstall with linux-image and it worked, but I had another problem now. 

When Ubuntu starts, it goes to the login screen and I can enter my pass. After I do, it shows the defang background and a dialog pops up that says "Could not update ICEauthority file /home/maclm01/.ICEauthority". Then I get one that says "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)". Then I get that says "Nautilus could not recreate the following home folders: Desktop, .nautilus." Then I get the first time run ecryptfs record your passphrase box. Could the fact that I mounted and unencrypted my home directory from the Live CD have anything to do with it? I ran chown maclm01 -R /home/maclm01 from the Live CD to see if that would fix it but it didn't change anything.

I read a thread about .ICEauthority problems yesterday. There were quite a few users with the problem when they installed 11.04. I would try to find that thread to see if anyone has found a solution. I think some of the users installed lxde and then reverted to the original and it worked.
Since the problem wasn't affecting my laptop and I'm on vacation I moved on to other threads.

If you can't find that thread I'd start a new one specifically about your current problem, since this title won't get you the helpers you really need to assist you.

---

### Post by electricmaster on 2011-05-04
Okay. Well thanks for the help. I'll take a look to see if I can find a fix.

---

