---
title: "cleaning up grub, and requesting dual boot guide."
date: 2011-04-17
forum: General Help
---

### Post by bryanftw on 2011-04-17
After lost of frustration last week of trying to get my messy dual boot to work properly, I decided to just restart all over, and just salvage my music. I installed ubuntu over my old windows 7 partition and deleted the old ubuntu 10.04 partition. 

Knowing this probably wasnt the best way to get it off, I was just very frustrated and probably made a quick decision. Whats done is done, but now grub is pretty messy. It lists it off as I have 3 versions of ubuntu installed. How do I get it to recognize that I only have 1 os, and do I have to clean up from a messy format. 

And also, I got a new windows 7 disc and I was looking a good dual boot guide with ubuntu already installed.

---

### Post by bryanftw on 2011-04-17
bump

---

### Post by Leppie on 2011-04-17
could you download the boot info script and post the generated results.txt: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Polluted13 on 2011-04-17
Hey, while we're on the topic of GRUB, maybe someone can help me out too.  I hate to hijack, but people get so bitchy when you start a new thread around here sometimes.

I did something similar to OP in that I decided to get rid of Windows and go to an Ubuntu only setup.  My problem now is that when I go to boot up I get a "no bootable device" message.

The only way I can boot up is by popping in an old Ubuntu CD I had and choosing "boot from first hard disc" in the menu.

It's been like this for a damned long time and I've just been too lazy to fix it.

Little help?  Thanks.

---

### Post by Leppie on 2011-04-17
Polluted, get the boot info script as well and post the output.

---

### Post by bryanftw on 2011-04-17
Having a problem running the script
I put ```
sudo bash boot_info_script055.sh
``` in the terminal but I get
```
bash: boot_info_script055.sh: No such file or directory

```
what am I doing wrong?

---

### Post by Leppie on 2011-04-17
try like this:
```
sudo bash Downloads/boot*.sh
```

---

### Post by bryanftw on 2011-04-17
thanks!
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 679495680 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb5: _________________________________________________________________________

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

/dev/sda1    *          2,048   378,884,095   378,882,048  83 Linux
/dev/sda2         378,886,142   390,721,535    11,835,394   5 Extended
/dev/sda5         378,886,144   390,721,535    11,835,392  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34       262,177       262,144 Microsoft Windows
/dev/sdb2         262,178   679,494,365   679,232,188 Linux or Data
/dev/sdb3     679,495,680   679,497,727         2,048 Linux or Data
/dev/sdb4     679,497,728   964,937,727   285,440,000 Linux or Data
/dev/sdb5     964,937,728   976,773,119    11,835,392 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        cdf105af-751f-4149-83c3-57a12f894b7d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5261825f-c6a4-48c4-89a6-320941cf2953   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2        16AB131F75B3A2EB                       ntfs       msf                           
/dev/sdb4        b4e34baa-54e7-457a-a6e7-234de0c1e083   ext4                                     
/dev/sdb5        76f9bab4-b43f-4b6d-95f5-7385e0f18eab   swap                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Windows 7 Ultim   udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=cdf105af-751f-4149-83c3-57a12f894b7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=cdf105af-751f-4149-83c3-57a12f894b7d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=cdf105af-751f-4149-83c3-57a12f894b7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=cdf105af-751f-4149-83c3-57a12f894b7d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sdb4)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sdb4)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb4)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sdb4)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=5261825f-c6a4-48c4-89a6-320941cf2953 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 122.5GB: boot/grub/core.img
  81.8GB: boot/grub/grub.cfg
 122.5GB: boot/initrd.img-2.6.32-28-generic
 122.6GB: boot/initrd.img-2.6.32-30-generic
    .2GB: boot/vmlinuz-2.6.32-28-generic
 122.5GB: boot/vmlinuz-2.6.32-30-generic
 122.6GB: initrd.img
 122.5GB: initrd.img.old
 122.5GB: vmlinuz
    .2GB: vmlinuz.old

=========================== sdb4/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_msdos
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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a224afe124afb727
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb4 during installation
UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=76f9bab4-b43f-4b6d-95f5-7385e0f18eab none            swap    sw              0       0

=================== sdb4: Location of files loaded by Grub: ===================


 457.5GB: boot/grub/core.img
 455.6GB: boot/grub/grub.cfg
 457.7GB: boot/initrd.img-2.6.32-28-generic
 457.6GB: boot/initrd.img-2.6.32-30-generic
 457.5GB: boot/vmlinuz-2.6.32-28-generic
 457.5GB: boot/vmlinuz-2.6.32-30-generic
 457.6GB: initrd.img
 457.7GB: initrd.img.old
 457.5GB: vmlinuz
 457.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  fe 32 bc 7f ec 44 2c f7  a2 0f 0e 2f 38 cf 9d fa  |.2...D,..../8...|
00000010  f6 3c 7d f0 cd dd 5f f8  80 68 37 8c 3c 05 47 ff  |.<}..._..h7.<.G.|
00000020  fc a0 c4 60 b1 0a 13 0c  16 d6 aa e2 79 27 e3 52  |...`........y'.R|
00000030  ba 6c 66 41 22 10 df 9c  95 0d 71 7b d7 9c 5a 77  |.lfA".....q{..Zw|
00000040  7c dd 95 f5 ff 2e 71 98  39 1b a7 70 6f e6 b4 b4  ||.....q.9..po...|
00000050  f4 6f 23 e0 5f e1 8d 20  11 19 e9 e1 dd b6 60 17  |.o#._.. ......`.|
00000060  6a e9 a1 a8 68 02 6e 86  8f 51 1c 7a e5 13 32 15  |j...h.n..Q.z..2.|
00000070  de 93 08 23 62 e1 70 64  d5 83 94 2d 06 be 82 f6  |...#b.pd...-....|
00000080  5a 1d 56 8e b5 58 e5 be  4b 3b 00 d9 01 c6 5a 50  |Z.V..X..K;....ZP|
00000090  62 67 67 24 36 2b 87 43  3f 03 af b1 d2 ab 7d 79  |bgg$6+.C?.....}y|
000000a0  69 44 c4 f4 2f c0 5f bd  57 b7 69 2b 3f f3 9d 45  |iD../._.W.i+?..E|
000000b0  58 7c cb 7b da 37 f2 0c  a0 66 79 5a de 78 f7 10  |X|.{.7...fyZ.x..|
000000c0  18 e9 b7 77 83 97 3f 7a  d7 2f db dc 24 92 89 5e  |...w..?z./..$..^|
000000d0  42 7f 47 a8 a5 e8 71 c0  f3 c7 6c ea 34 78 37 6c  |B.G...q...l.4x7l|
000000e0  02 24 68 71 ce 08 88 3a  be 00 7e 46 36 9b ac 1a  |.$hq...:..~F6...|
000000f0  bd 90 12 66 95 26 c4 25  4b 32 8a 4c e5 1a 45 66  |...f.&.%K2.L..Ef|
00000100  83 c1 da 51 7d b0 96 a3  39 1f 5e 62 5c 42 f6 f3  |...Q}...9.^b\B..|
00000110  9f 2c 01 ff 26 2e cf 2a  ce 2c ca 12 f8 e0 8c 0a  |.,..&..*.,......|
00000120  64 0c b9 a0 8a f3 c9 23  04 83 6c 3d af ac 36 12  |d......#..l=..6.|
00000130  d5 e6 1a 73 d0 47 ae 3f  b8 71 23 71 7d c1 38 e1  |...s.G.?.q#q}.8.|
00000140  32 ad 27 07 8d df 43 55  30 54 ca 18 cc cc 0f b6  |2.'...CU0T......|
00000150  7d 2d 7c c7 da 9b 30 35  62 82 f0 42 c5 60 15 f3  |}-|...05b..B.`..|
00000160  1e 1b 9c 49 b9 ed 36 cf  71 38 c4 57 a0 d5 1b 34  |...I..6.q8.W...4|
00000170  7a 8b 81 ad 50 ed 2c 6b  8f 71 23 c3 c2 3a 8d ac  |z...P.,k.q#..:..|
00000180  52 3a 62 9a e8 d9 31 54  b1 dd a1 b1 2b ed 95 f6  |R:b...1T....+...|
00000190  ca c3 a3 6a 8a 8b ad da  32 56 e5 d1 7b ca 3d 6a  |...j....2V..{.=j|
000001a0  09 58 75 96 32 e3 68 13  c5 7d 56 9d 01 f9 e1 0a  |.Xu.2.h..}V.....|
000001b0  2c db b4 96 48 ce cb d7  26 2a d5 c5 66 73 00 fe  |,...H...&*..fs..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 b4 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb3

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 48 80 28  00 00 00 00 2f 00 20 08  |.....H.(..../. .|
00000200


```

---

### Post by Leppie on 2011-04-17
it looks like you  did not install over your windows 7, however its boot partition (sdb1) seems damaged.
if you want, you could use the new windows disk to restore your windows installation (more information here: [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD))

if you want to delete your old lucid install, you can use applications like gparted to remove the partitions used by lucid and format them as ntfs to use with both windows and your new install.

---

### Post by oldfred on 2011-04-17
@bryanftw
Your 500GB drive is gpt, but you have a windows install?? Windows only boots from gpt if you have win7 64bit and use UEFI not BIOS. Ubuntu (newer versions) works great on gpt drives.

It looks like sdb1 should be a bios_grub partition so grub2 has a place to install with gpt.

@Polluted13
Please do not post boot script here as it will get too confusing. Try this, if not start a new thread and post boot script.
Boot into your working system:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda

---

### Post by bryanftw on 2011-04-17
Well I did what you say, but when I load up my computer, it still gives me the option of choosing 3 different ubuntu's. (not talking about the memtests or the recovery modes, those are also there).
Theres just a lot of clutter there and Im wondering where its from.

heres the latest boot info. 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 679495680 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   378,884,095   378,882,048  83 Linux
/dev/sda2         378,886,142   390,721,535    11,835,394   5 Extended
/dev/sda5         378,886,144   390,721,535    11,835,392  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34   976,768,064   976,768,031 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        cdf105af-751f-4149-83c3-57a12f894b7d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5261825f-c6a4-48c4-89a6-320941cf2953   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3BFAA1E668F097BB                       ntfs       Storage                       
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=cdf105af-751f-4149-83c3-57a12f894b7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=cdf105af-751f-4149-83c3-57a12f894b7d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=cdf105af-751f-4149-83c3-57a12f894b7d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=cdf105af-751f-4149-83c3-57a12f894b7d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdf105af-751f-4149-83c3-57a12f894b7d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sdb4)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sdb4)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb4)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sdb4)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=5261825f-c6a4-48c4-89a6-320941cf2953 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 122.5GB: boot/grub/core.img
  81.8GB: boot/grub/grub.cfg
 122.5GB: boot/initrd.img-2.6.32-28-generic
 122.6GB: boot/initrd.img-2.6.32-30-generic
    .2GB: boot/vmlinuz-2.6.32-28-generic
 122.5GB: boot/vmlinuz-2.6.32-30-generic
 122.6GB: initrd.img
 122.5GB: initrd.img.old
 122.5GB: vmlinuz
    .2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  fe 32 bc 7f ec 44 2c f7  a2 0f 0e 2f 38 cf 9d fa  |.2...D,..../8...|
00000010  f6 3c 7d f0 cd dd 5f f8  80 68 37 8c 3c 05 47 ff  |.<}..._..h7.<.G.|
00000020  fc a0 c4 60 b1 0a 13 0c  16 d6 aa e2 79 27 e3 52  |...`........y'.R|
00000030  ba 6c 66 41 22 10 df 9c  95 0d 71 7b d7 9c 5a 77  |.lfA".....q{..Zw|
00000040  7c dd 95 f5 ff 2e 71 98  39 1b a7 70 6f e6 b4 b4  ||.....q.9..po...|
00000050  f4 6f 23 e0 5f e1 8d 20  11 19 e9 e1 dd b6 60 17  |.o#._.. ......`.|
00000060  6a e9 a1 a8 68 02 6e 86  8f 51 1c 7a e5 13 32 15  |j...h.n..Q.z..2.|
00000070  de 93 08 23 62 e1 70 64  d5 83 94 2d 06 be 82 f6  |...#b.pd...-....|
00000080  5a 1d 56 8e b5 58 e5 be  4b 3b 00 d9 01 c6 5a 50  |Z.V..X..K;....ZP|
00000090  62 67 67 24 36 2b 87 43  3f 03 af b1 d2 ab 7d 79  |bgg$6+.C?.....}y|
000000a0  69 44 c4 f4 2f c0 5f bd  57 b7 69 2b 3f f3 9d 45  |iD../._.W.i+?..E|
000000b0  58 7c cb 7b da 37 f2 0c  a0 66 79 5a de 78 f7 10  |X|.{.7...fyZ.x..|
000000c0  18 e9 b7 77 83 97 3f 7a  d7 2f db dc 24 92 89 5e  |...w..?z./..$..^|
000000d0  42 7f 47 a8 a5 e8 71 c0  f3 c7 6c ea 34 78 37 6c  |B.G...q...l.4x7l|
000000e0  02 24 68 71 ce 08 88 3a  be 00 7e 46 36 9b ac 1a  |.$hq...:..~F6...|
000000f0  bd 90 12 66 95 26 c4 25  4b 32 8a 4c e5 1a 45 66  |...f.&.%K2.L..Ef|
00000100  83 c1 da 51 7d b0 96 a3  39 1f 5e 62 5c 42 f6 f3  |...Q}...9.^b\B..|
00000110  9f 2c 01 ff 26 2e cf 2a  ce 2c ca 12 f8 e0 8c 0a  |.,..&..*.,......|
00000120  64 0c b9 a0 8a f3 c9 23  04 83 6c 3d af ac 36 12  |d......#..l=..6.|
00000130  d5 e6 1a 73 d0 47 ae 3f  b8 71 23 71 7d c1 38 e1  |...s.G.?.q#q}.8.|
00000140  32 ad 27 07 8d df 43 55  30 54 ca 18 cc cc 0f b6  |2.'...CU0T......|
00000150  7d 2d 7c c7 da 9b 30 35  62 82 f0 42 c5 60 15 f3  |}-|...05b..B.`..|
00000160  1e 1b 9c 49 b9 ed 36 cf  71 38 c4 57 a0 d5 1b 34  |...I..6.q8.W...4|
00000170  7a 8b 81 ad 50 ed 2c 6b  8f 71 23 c3 c2 3a 8d ac  |z...P.,k.q#..:..|
00000180  52 3a 62 9a e8 d9 31 54  b1 dd a1 b1 2b ed 95 f6  |R:b...1T....+...|
00000190  ca c3 a3 6a 8a 8b ad da  32 56 e5 d1 7b ca 3d 6a  |...j....2V..{.=j|
000001a0  09 58 75 96 32 e3 68 13  c5 7d 56 9d 01 f9 e1 0a  |.Xu.2.h..}V.....|
000001b0  2c db b4 96 48 ce cb d7  26 2a d5 c5 66 73 00 fe  |,...H...&*..fs..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 b4 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2011-04-17
If you update your grub does it erase some old data?
```

sudo update-grub
```

---

### Post by bryanftw on 2011-04-17
> **oldfred said:**
> If you update your grub does it erase some old data?
```

sudo update-grub
```
Tried this like 5 minutes before you posted and it worked. good stuff thanks

---

