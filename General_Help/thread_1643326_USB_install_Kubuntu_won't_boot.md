---
title: "USB install Kubuntu won't boot"
date: 2010-12-11
forum: General Help
---

### Post by bachor on 2010-12-11
I did install Kubuntu 10.10 LVM  Encrypted from Alternate CD on dual boot XP with Ubuntu 10.10.

[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")

 My problem is,that when installation asked me for where to put GRUB I didn't type anything because I have GRUB2 already installed.

 Now it won't boot. Tried Bios to set USB as 1st boot,and HDD as a 2nd option. It went to 2nd option,with GRUB2.

 So I hit "c" and "ls" showed only HD0 and HD1 (HD has 2 partitions,1st XP and 2nd Ubuntu 10] and no SD found.:o

 How can I fix this? 

 Installation took for hours,would be nice to fix it without reinstalling it again :D

---

### Post by Quackers on 2010-12-11
Try booting into your original installation (the one which did install grub2) and run sudo update-grub. Then watch to see if your kubuntu install is picked up.

---

### Post by bachor on 2010-12-12
> **Quackers said:**
> Try booting into your original installation (the one which did install grub2) and run sudo update-grub. Then watch to see if your kubuntu install is picked up.

tried sudo update-grub and got
grub> unknown command `sudo'

also USB flash is Cruzer Micro 8gb,which has partition 100mb with U3 software for windoze . I wasn't able to erase it anyhow.

---

### Post by sikander3786 on 2010-12-12
From that Grub> otuput, I suspect that there is Grub Legacy installed and not Grub2.

To give us a better look of your setup, please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

---

### Post by bachor on 2010-12-12
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   BLKID Error_Log Log Log1 
                       Mount_Error PT sda1 sda2 sda5 sda6 Tmp_Log Trash 
                       NOTICE TO USERS This computer system is the private 
                       property of The owner, whether individual, corporate 
                       or government. It is for authorized use only. Users 
                       (authorized or unauthorized) have no explicit or 
                       implicit expectation of privacy. Any or all uses of 
                       this system and all files on this system may be 
                       intercepted, monitored, recorded, copied, audited, 
                       inspected, and disclosed to your employer, to 
                       authorized site, government, and law enforcement 
                       personnel, as well as authorized officials of 
                       government agencies, both domestic and foreign. By 
                       using this system, the user consents to such 
                       interception, monitoring, recording, copying, 
                       auditing, inspection, and disclosure at the discretion 
                       of such personnel or officials. Unauthorized or 
                       improper use of this system may result in civil and 
                       criminal penalties and administrative or disciplinary 
                       action, as appropriate. By continuing to use this 
                       system you indicate your awareness of and consent to 
                       these terms and conditions of use. LOG OFF IMMEDIATELY 
                       if you do not agree to the conditions stated in this 
                       warning. BLKID Error_Log Log Log1 Mount_Error PT sda1 
                       sda2 sda5 sda6 Tmp_Log Trash
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,382,884    29,382,822   7 HPFS/NTFS
/dev/sda2          29,382,946   234,440,703   205,057,758   f W95 Ext d (LBA)
/dev/sda5          29,382,948   193,486,859   164,103,912   b W95 FAT32
/dev/sda6         193,488,896   230,533,119    37,044,224  83 Linux
/dev/sda7         230,535,168   234,440,703     3,905,536  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8036 MB, 8036285952 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048       499,711       497,664  83 Linux
/dev/sdb2             501,758    15,693,823    15,192,066   5 Extended
/dev/sdb5             501,760    15,693,823    15,192,064  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        01CA31A03493A4A0                       ntfs       XP                            
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4AA8-1A27                              vfat                                     
/dev/sda6        e1a6c85d-59e6-4666-af0b-9780a35b3c94   ext4                                     
/dev/sda7        43bcb405-2d85-4c77-a753-1f31c8eb058b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        22aed5fd-1d59-4664-a0f3-5379e6509f27   ext2                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        01b2f935-2fd5-49ac-9bcb-539c730f8f6d   crypto_LUKS                               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/22aed5fd-1d59-4664-a0f3-5379e6509f27 ext2       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
insmod tga
if background_image /usr/share/images/grub/Lake_mapourika_NZ.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro  splash vga=788  quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro single  splash vga=788
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro  splash vga=788  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro single  splash vga=788
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
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01ca31a03493a4a0
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=43bcb405-2d85-4c77-a753-1f31c8eb058b none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 112.1GB: boot/grub/core.img
 114.6GB: boot/grub/grub.cfg
 115.1GB: boot/initrd.img-2.6.35-22-generic
 115.8GB: boot/initrd.img-2.6.35-23-generic
 112.5GB: boot/vmlinuz-2.6.35-22-generic
 112.9GB: boot/vmlinuz-2.6.35-23-generic
 115.8GB: initrd.img
 115.1GB: initrd.img.old
 112.9GB: vmlinuz
 112.5GB: vmlinuz.old

============================= sdb1/grub/grub.cfg: =============================

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
}

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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 22aed5fd-1d59-4664-a0f3-5379e6509f27
    linux    /vmlinuz-2.6.35-22-generic root=/dev/mapper/ubuntu-root ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 22aed5fd-1d59-4664-a0f3-5379e6509f27
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=/dev/mapper/ubuntu-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 22aed5fd-1d59-4664-a0f3-5379e6509f27
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 22aed5fd-1d59-4664-a0f3-5379e6509f27
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01ca31a03493a4a0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro splash vga=788 quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro single splash vga=788
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro splash vga=788 quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e1a6c85d-59e6-4666-af0b-9780a35b3c94
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=e1a6c85d-59e6-4666-af0b-9780a35b3c94 ro single splash vga=788
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

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  d3 7b 0c a2 e9 0d 41 3a  73 35 2d a4 bb 3f f0 79  |.{....A:s5-..?.y|
00000010  b4 3f f0 87 e4 1b c9 cc  0c ec 34 db 04 b4 dc eb  |.?........4.....|
00000020  0e a7 bb 8d 49 0e d2 d8  91 75 b9 6a 21 40 d3 83  |....I....u.j!@..|
00000030  2f c6 e9 66 e5 64 f6 72  f0 88 3c 62 39 80 a8 a1  |/..f.d.r..<b9...|
00000040  ac e2 1e fa 9b 72 cb 4f  7b 5b b5 07 07 f9 0c e8  |.....r.O{[......|
00000050  43 7c 8d 39 fe 42 65 da  ac e6 c6 da 9d 9b 82 1f  |C|.9.Be.........|
00000060  94 99 16 7f 8c b5 c0 9c  1f a2 a7 e3 6b 6a 4f c0  |............kjO.|
00000070  51 0a 6d 45 68 b7 93 0c  e2 db a2 7b a2 ab b2 2e  |Q.mEh......{....|
00000080  69 11 97 86 41 d6 0b 8e  2b be 88 90 63 b5 9d dd  |i...A...+...c...|
00000090  d7 c1 57 91 84 c7 61 d2  7a ea 29 a3 b7 02 e4 37  |..W...a.z.)....7|
000000a0  ee df 82 45 f0 06 08 e3  dc 79 3d 15 04 7d 12 d2  |...E.....y=..}..|
000000b0  4a d1 7b cb d2 6a 06 ff  9c c3 1b 87 8b fd e1 12  |J.{..j..........|
000000c0  3c 84 89 5d 77 54 36 0f  7c 40 0f 25 79 79 02 4e  |<..]wT6.|@.%yy.N|
000000d0  2a 6b 8b ef 9a 92 e9 b1  97 46 53 15 75 88 3f e3  |*k.......FS.u.?.|
000000e0  49 5c 11 75 83 27 97 9b  ba af 6e 3e b6 fa e9 c4  |I\.u.'....n>....|
000000f0  a4 76 69 bc f9 9d 65 dc  0d d3 c8 0d e7 8a d4 10  |.vi...e.........|
00000100  1d ff 02 0f eb 7a a2 41  97 81 93 32 ae 39 36 44  |.....z.A...2.96D|
00000110  c3 44 fa db 91 56 2f 3c  2e b9 b8 87 15 4f 56 09  |.D...V/<.....OV.|
00000120  4a 58 16 d3 a4 38 8c 04  42 89 7f d6 7d 8c d0 ca  |JX...8..B...}...|
00000130  7e 43 de 14 a7 ab 2a b7  a6 fa 34 54 be 1b 97 d2  |~C....*...4T....|
00000140  11 45 cd 58 2a 33 64 bd  1b 88 16 73 fd ae f0 fc  |.E.X*3d....s....|
00000150  0d b9 4c a2 f1 37 da 5e  97 c4 ca 93 4f cb 8f 31  |..L..7.^....O..1|
00000160  7b 87 c3 27 1a b1 5d 27  87 f1 7d ab c7 8f f0 0f  |{..'..]'..}.....|
00000170  90 27 f1 47 1d 31 b5 4c  4c 9f 1a 3d 59 3d 3a 45  |.'.G.1.LL..=Y=:E|
00000180  b9 14 84 4d c2 73 bc d5  cb d8 56 dd 02 ef 3d 5a  |...M.s....V...=Z|
00000190  90 48 ef 1d d2 db 94 b8  9a 50 fc d1 ab 45 fe 2b  |.H.......P...E.+|
000001a0  cb f9 b9 f8 34 e2 e3 e9  cc 44 db 8f f3 a2 cf dd  |....4....D......|
000001b0  59 26 b9 bc 0c ec ef 16  79 42 33 b5 d1 94 00 3b  |Y&......yB3....;|
000001c0  1d 1f 83 e4 d4 d0 02 00  00 00 00 d0 e7 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb5

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  ae 3f da 51 d1 88 cb c2  5e c4 df ef 98 48 e5 51  |.?.Q....^....H.Q|
00000080  4d 41 6f 9b ec 9e 74 10  e5 a3 57 6d 53 f4 96 e2  |MAo...t...WmS...|
00000090  c4 91 e1 d5 be b7 24 5c  d9 0a dc 56 fc bd 92 30  |......$\...V...0|
000000a0  92 70 11 2a 00 00 4d 26  30 31 62 32 66 39 33 35  |.p.*..M&01b2f935|
000000b0  2d 32 66 64 35 2d 34 39  61 63 2d 39 62 63 62 2d  |-2fd5-49ac-9bcb-|
000000c0  35 33 39 63 37 33 30 66  38 66 36 64 00 00 00 00  |539c730f8f6d....|
000000d0  00 ac 71 f3 00 01 36 82  b1 80 ad ba 79 ef 10 9b  |..q...6.....y...|
000000e0  fe 6a 06 e0 77 e3 29 eb  d2 4c a5 04 43 b5 10 d0  |.j..w.)..L..C...|
000000f0  50 f7 ee 62 1b c9 2b be  00 00 00 08 00 00 0f a0  |P..b..+.........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


```

---

### Post by bachor on 2010-12-13
is there a command to wipe WHOLE flash partitions with that U3 System?

I've tried rm U3 or change permission and it wouldn't let me. 

Or is it OK to leave U3 and reinstall it again? I wonder it that U3 isn't the reason why it won't boot.

might be easier start all over

---

### Post by bachor on 2010-12-13
Ok,googled and found U3 removal tool from Sandisk web page [for XP].
Removed its utility and erased whole flash drive. Ready for clean Kubuntu install :D

---

