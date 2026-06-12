---
title: "Ubuntu crashed, help!"
date: 2010-12-22
forum: General Help
---

### Post by PerSeL on 2010-12-22
Hello,
I have installed Ubuntu 10.10 on my laptop Sony Vaio VGN-CR123e before reformat my laptop. I did like it and decided to make a dual boot. so I made a clean setup of my MS Windows 7 and installed Ubuntu on 45GB. after 2-3 days of using it crashed, I couldn't expect that... is it usually happens to Ubuntu? as far as I know linux made for stability.

it gives me the next screen (I hope I copied it right):
[0.852036] Kernel Panic - not syncing:VFS:Unable to mount root fs on unknown-block(0,0)
[0.852084] Pid:1, comm:swapper not trained 2.6.35-24-generic #42-Ubuntu
[0.852130] Call Trace:
[0.852172] [<c05c707f>] ? printk+0x2d/0x36
[0.852210] [<c05c6fda>] panic+0x5a/0xd2
[0.852250] [<c05c707f>] mount_block_root+0x1d3/0x26c
[0.852290] [<c05c707f>] ? sys_mknod+0x2c/0x30
[0.852329] [<c05c707f>] mount_root+0x59/0x5f
[0.852368] [<c05c707f>] prepare_namespace+0x14e/0x192
[0.852409] [<c05c707f>] ? sys_access+0x25/0x30
[0.852448] [<c05c707f>] kernel_init+0x18e/0x19d
[0.852486] [<c05c707f>] ? kernel+init+0x0/0x19d
[0.852525] [<c05c707f>] kernel_thread_helper+0x6/0x10

---

### Post by PerSeL on 2010-12-23
bump....

now i reinstalled ubuntu and it freezed after i it ejected the cd and also my computer don't want to load ubuntu... have it killed my laptop?

---

### Post by Quackers on 2010-12-23
Do you have a Windows repair disc? (Not a recovery dvd)

---

### Post by PerSeL on 2010-12-23
> **Quackers said:**
> Do you have a Windows repair disc? (Not a recovery dvd) no I have clean setup cd

---

### Post by Quackers on 2010-12-23
Is that a normal installation dvd?

---

### Post by PerSeL on 2010-12-23
> **Quackers said:**
> Is that a normal installation dvd?
Yes it original 7 I don't  mind to format again anyway I just made 2 days ago a format and made it dual boot with ubuntu... but I don't want ubuntu to crash without a reason.

---

### Post by Quackers on 2010-12-23
You shouldn't need to re-install Windows. You should be able to get Windows back by booting from the Windows disc and selecting the repair option and then running Startup Repair. It may need to run up to 3 times to repair the boot sequence properly.

I don't know why Ubuntu gave you a kernel panic. That may be something to look at later. If you get Windows back up at least you'll have a system to work with.

Please let me know how that goes.

---

### Post by PerSeL on 2010-12-23
the windows is working but 2 ubuntu partitios not (the one I've installed 2 days ago and suddenly after restart crashed and the other one that I installed 30 mins ago)

---

### Post by Quackers on 2010-12-23
Ah, ok.
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

---

### Post by PerSeL on 2010-12-23
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

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

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   134,610,141   134,403,294   7 HPFS/NTFS
/dev/sda3         134,610,942   312,580,095   177,969,154   5 Extended
/dev/sda5         224,530,432   308,881,407    84,350,976  83 Linux
/dev/sda6         308,883,456   312,580,095     3,696,640  82 Linux swap / Solaris
/dev/sda7         134,610,944   220,753,919    86,142,976  83 Linux
/dev/sda8         220,755,968   224,524,287     3,768,320  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6EA256DFA256AB7B                       ntfs       System Reserved               
/dev/sda2        0C545D8A545D7782                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        212ead2c-698e-4d85-ba10-00858802dab3   ext4                                     
/dev/sda6        2531efca-6bf2-47f3-8373-ac876031dc68   swap                                     
/dev/sda7        0e8bc004-5567-43d1-bab6-ae7615b3d58c   ext4                                     
/dev/sda8        0a6423c0-0aee-4488-848a-81a1d26e02c9   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=212ead2c-698e-4d85-ba10-00858802dab3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=212ead2c-698e-4d85-ba10-00858802dab3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=212ead2c-698e-4d85-ba10-00858802dab3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=212ead2c-698e-4d85-ba10-00858802dab3 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6ea256dfa256ab7b
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
UUID=212ead2c-698e-4d85-ba10-00858802dab3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2531efca-6bf2-47f3-8373-ac876031dc68 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 119.3GB: boot/grub/core.img
 143.1GB: boot/grub/grub.cfg
 115.7GB: boot/initrd.img-2.6.35-22-generic
 116.5GB: boot/initrd.img-2.6.35-24-generic
 119.3GB: boot/vmlinuz-2.6.35-22-generic
 119.4GB: boot/vmlinuz-2.6.35-24-generic
 116.5GB: initrd.img
 115.7GB: initrd.img.old
 119.4GB: vmlinuz
 119.3GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 0e8bc004-5567-43d1-bab6-ae7615b3d58c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 0e8bc004-5567-43d1-bab6-ae7615b3d58c
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 0e8bc004-5567-43d1-bab6-ae7615b3d58c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0e8bc004-5567-43d1-bab6-ae7615b3d58c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 0e8bc004-5567-43d1-bab6-ae7615b3d58c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0e8bc004-5567-43d1-bab6-ae7615b3d58c ro single 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 0e8bc004-5567-43d1-bab6-ae7615b3d58c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 0e8bc004-5567-43d1-bab6-ae7615b3d58c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6ea256dfa256ab7b
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=212ead2c-698e-4d85-ba10-00858802dab3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=212ead2c-698e-4d85-ba10-00858802dab3 ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=212ead2c-698e-4d85-ba10-00858802dab3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 212ead2c-698e-4d85-ba10-00858802dab3
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=212ead2c-698e-4d85-ba10-00858802dab3 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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
UUID=0e8bc004-5567-43d1-bab6-ae7615b3d58c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=0a6423c0-0aee-4488-848a-81a1d26e02c9 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  96.9GB: boot/grub/core.img
 109.8GB: boot/grub/grub.cfg
  69.7GB: boot/initrd.img-2.6.35-22-generic
  69.2GB: boot/vmlinuz-2.6.35-22-generic
  69.7GB: initrd.img
  69.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  16 a4 54 42 47 c5 27 6d  38 15 36 de b1 c5 8e 93  |..TBG.'m8.6.....|
00000010  b7 64 e1 4f 5d c8 d0 04  e2 ad e8 4a 3b e2 82 6c  |.d.O]......J;..l|
00000020  17 8a 7a 9c 67 d6 c6 58  38 70 57 b1 61 2c 79 02  |..z.g..X8pW.a,y.|
00000030  c4 cf c5 f2 86 42 f3 22  f7 0a 92 3f 1c 2b 38 d1  |.....B."...?.+8.|
00000040  c1 5f 26 30 2d 38 36 f5  ef 14 e7 8c b9 08 50 09  |._&0-86.......P.|
00000050  73 2b 34 f5 18 88 f6 c2  76 42 66 b4 f3 d3 9e 0a  |s+4.....vBf.....|
00000060  d8 0b f2 91 1b 9d 36 f1  7b 34 d0 96 dc 7e b3 08  |......6.{4...~..|
00000070  c4 3a d1 64 3c f4 64 a2  d1 99 15 a3 24 70 fe bd  |.:.d<.d.....$p..|
00000080  8d fc 2b 59 30 65 a2 e0  a1 fb c1 a8 aa 36 13 93  |..+Y0e.......6..|
00000090  05 09 9e 34 35 3d 91 c2  a0 a2 93 8f ac 19 c7 13  |...45=..........|
000000a0  85 36 d3 87 47 89 f3 b9  bc c3 c9 4c 24 44 2e 34  |.6..G......L$D.4|
000000b0  2b 74 e1 8b 67 c4 d9 2c  de 3c 47 80 dc 3e f3 10  |+t..g..,.<G..>..|
000000c0  e8 5b cf c1 83 c2 b7 92  23 16 39 e2 4e a7 79 fa  |.[......#.9.N.y.|
000000d0  58 7c 2a 6b 96 80 d1 af  16 60 a9 dd 3c da 6e 17  |X|*k.....`..<.n.|
000000e0  8a 04 16 2d 15 fc 0c 3c  6d 44 82 94 8d 70 eb 0e  |...-...<mD...p..|
000000f0  b4 c0 ad b7 78 5c 2d b2  61 6c 9d 8a d5 ce 16 57  |....x\-.al.....W|
00000100  0a 1a 38 e0 bf 8e 3e 16  8e e4 a4 a7 45 79 21 d1  |..8...>.....Ey!.|
00000110  1a 4c 3e 1a 27 e0 44 06  46 22 3e 8b 13 85 78 63  |.L>.'.D.F">...xc|
00000120  79 c2 16 94 9c 0a 9b 27  1f 6e 50 63 58 4a 2a cf  |y......'.nPcXJ*.|
00000130  0d 45 e4 ca 32 71 18 5f  73 c7 e7 eb 66 d8 cc c5  |.E..2q._s...f...|
00000140  4c 9d 86 c7 a3 26 5d 4f  9f 0a 57 fa c4 50 5a 26  |L....&]O..W..PZ&|
00000150  26 26 0a 6a 80 87 0b 06  0c 12 d2 70 30 1c 9e 14  |&&.j.......p0...|
00000160  0c 8a d1 06 9c 16 3c 42  de 2d c7 b3 d2 71 17 aa  |......<B.-...q..|
00000170  05 60 2b a0 3d b3 21 49  a4 34 4b 06 e6 66 14 0a  |.`+.=.!I.4K..f..|
00000180  ce 8a 72 22 78 4c 21 e2  d2 76 4f a9 d9 31 25 1a  |..r"xL!..vO..1%.|
00000190  08 fa c0 52 48 40 2c 51  6f 51 8b c5 79 08 c4 5f  |...RH@,QoQ..y.._|
000001a0  0c 0b a2 30 a9 37 1b ab  3c 6a 17 cd 9a 10 cd 3c  |...0.7..<j.....<|
000001b0  6a 64 d3 04 de 17 c0 b1  13 c5 e7 05 f4 33 00 fe  |jd...........3..|
000001c0  ff ff 83 fe ff ff 02 10  5c 05 00 18 07 05 00 fe  |........\.......|
000001d0  ff ff 05 fe ff ff 5d 29  63 0a a5 6e 38 00 00 00  |......])c..n8...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by PerSeL on 2010-12-24
bump anyone?

---

### Post by johnmay on 2010-12-24
Have you tried booting with only the Ubuntu drive online? 

Also, It is my experience that some of the limited run or extreme CPU's don't like the out of the box linux configs

---

### Post by PerSeL on 2010-12-24
> **johnmay said:**
> Have you tried booting with only the Ubuntu drive online? 

Also, It is my experience that some of the limited run or extreme CPU's don't like the out of the box linux configsDo you mean the live cd? well if I couldn't I wouldn't make the boot info script.

also what do you mean by extreme CPU? it's only T7300

---

### Post by johnmay on 2010-12-24
I meant booting with only the ubuntu internal drive attached to the system to see if boot happens okay. 

about CPU's some hardware is not completely 'out of the box' linux friendly 

If your cpu is over clocked, or you have a weird BIOS setup, that could cause some difficulty.

---

### Post by PerSeL on 2010-12-24
> **johnmay said:**
> I meant booting with only the ubuntu internal drive attached to the system to see if boot happens okay. 

about CPU's some hardware is not completely 'out of the box' linux friendly 

If your cpu is over clocked, or you have a weird BIOS setup, that could cause some difficulty.So in generally you say that if I haven't touched my bios and my CPU isn't over clocked that means my computer cannot run linux?

---

### Post by Quackers on 2010-12-24
No, he is saying that if your bios is non-standard or if you're cpu is over-clocked it can cause problems.
I don't see anything wrong with the output of the boot script.
I suggest we try re-installing grub.
From the live cd desktop please open a terminal and copy/paste these lines in one at a time pressing enter after each line.
```
sudo mount /dev/sda7 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
```
Then reboot and see if Ubuntu boots directly.
This is using the later installation of Ubuntu. If you want to try the earlier one first change sda7 in the first command to sda5

---

### Post by PerSeL on 2010-12-25
hello and thanks for the support... I thought to gave all of that up and make a clean install without windows partition.

In the end of installation after the button restart in the black screen it wrote to me a whole list of errors / sectors - I wonder if my hard drive is damaged or it's a bad install disc. How can I check my hard drive with live cd

I removed again, evolution and firefox threw "Ubuntu Software Center" and updated and after this my Ubuntu crashed again... It's loading up but without any panel, and I also cannot create any.

---

