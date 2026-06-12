---
title: "Kernel panic - help! [Linux noob]"
date: 2011-02-01
forum: General Help
---

### Post by CowboyBoats on 2011-02-01
When I try to start my computer, I get the following error message after the GRUB screen:

```
[1.541831] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown un-block (0,0) 
```followed by a bunch of [code]("http://http://i.imgur.com/0zbnz.jpg").

I can boot from an Ubuntu Live CD, and access my files, but how can I get this OS running again? Should I just format and reinstall? Will that even work?

---

### Post by matt_symes on 2011-02-01
Hi

Can you boot into an old kernel from the grub menu ?

Kind regards

---

### Post by CowboyBoats on 2011-02-01
Hey Matt, thanks for posting. 

No, or I don't know how to do that. My options are boot into Ubuntu, boot into Ubuntu (recovery) (results in a similar error screen to what I posted) and two memory tests (which both say my memory is OK).

---

### Post by matt_symes on 2011-02-01
Hi

Sounds like you only have one kernel installed. Is this a recent install ?

It is good that you can boot into the memory tests. I think it might be worth having a look at your grub configuration.

From the LiveCD/USB run the boot info script in my signature. The instructions are on the web page. Post the results back here.

Kind regards

---

### Post by CowboyBoats on 2011-02-01
Here ya go:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,225,687,039 1,225,684,992  83 Linux
/dev/sda2       1,225,689,086 1,250,263,039    24,573,954   5 Extended
/dev/sda5       1,225,689,088 1,250,263,039    24,573,952  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8011 MB, 8011087872 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62    15,635,593    15,635,532   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       9d166c8f-01f4-40b0-9906-a604d2dd578e   ext3                                     
/dev/sda1        6bd2f44d-5752-48d6-bf98-cf1c036980fb   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c6f1f675-9fa1-43f5-9410-ece4807a27f5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EBCC-0609                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 6bd2f44d-5752-48d6-bf98-cf1c036980fb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 6bd2f44d-5752-48d6-bf98-cf1c036980fb
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6bd2f44d-5752-48d6-bf98-cf1c036980fb
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=6bd2f44d-5752-48d6-bf98-cf1c036980fb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6bd2f44d-5752-48d6-bf98-cf1c036980fb
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=6bd2f44d-5752-48d6-bf98-cf1c036980fb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6bd2f44d-5752-48d6-bf98-cf1c036980fb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6bd2f44d-5752-48d6-bf98-cf1c036980fb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
# / was on /dev/sda1 during installation
UUID=6bd2f44d-5752-48d6-bf98-cf1c036980fb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c6f1f675-9fa1-43f5-9410-ece4807a27f5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 309.3GB: boot/grub/core.img
 230.0GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-24-generic-pae
 309.3GB: boot/vmlinuz-2.6.35-24-generic-pae
    .9GB: initrd.img
 309.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  2f 9a 00 00 41 9e 00 44  7f a3 eb 78 7f 44 d3 78  |/...A..D...x.D.x|
00000010  4b ff f8 89 41 92 01 20  80 1d 00 f0 7f 9a 00 40  |K...A.. .......@|
00000020  41 9c 01 14 80 1d 00 f4  7f 9a 00 40 40 9c 01 08  |A..........@@...|
00000030  80 1d 00 ec 90 1a 00 00  93 5d 00 ec 80 5d 00 e4  |.........]...]..|
00000040  38 42 ff ff 90 5d 00 e4  38 60 00 00 93 7e 00 14  |8B...]..8`...~..|
00000050  48 00 01 3c 80 be 00 0c  7f 64 db 78 54 a0 28 34  |H..<.....d.xT.(4|
00000060  54 a5 18 38 7c a5 02 14  48 08 17 75 38 1e 00 18  |T..8|...H..u8...|
00000070  7f 80 d8 00 41 9e 00 40  41 92 00 c8 2f 9b 00 00  |....A..@A.../...|
00000080  41 9e 00 c0 80 1d 00 f0  7f 9b 00 40 41 9c 00 b4  |A..........@A...|
00000090  80 1d 00 f4 7f 9b 00 40  40 9c 00 a8 80 1d 00 ec  |.......@@.......|
000000a0  90 1b 00 00 93 7d 00 ec  80 5d 00 e4 38 42 ff ff  |.....}...]..8B..|
000000b0  90 5d 00 e4 81 7e 00 14  38 40 00 00 2f 8b 00 00  |.]...~..8@../...|
000000c0  41 9e 00 34 41 92 00 88  80 1d 00 f0 7f 8b 00 40  |A..4A..........@|
000000d0  41 9c 00 7c 80 1d 00 f4  7f 8b 00 40 40 9c 00 70  |A..|.......@@..p|
000000e0  a0 5d 00 e0 3c 00 cc cc  60 00 cc cd 7c 42 00 16  |.]..<...`...|B..|
000000f0  54 42 d9 7e 80 7e 00 0c  90 5e 00 10 48 00 00 08  |TB.~.~...^..H...|
00000100  81 7e 00 14 54 60 28 34  54 62 18 38 7c 42 02 14  |.~..T`(4Tb.8|B..|
00000110  38 03 00 01 90 1e 00 0c  7d 22 5a 14 38 00 ff ff  |8.......}"Z.8...|
00000120  7f 42 59 2e 90 09 00 04  9a e9 00 12 93 c9 00 14  |.BY.............|
00000130  48 00 00 5c 7f 43 d3 78  4b fd e3 21 4b ff ff 0c  |H..\.C.xK..!K...|
00000140  7f 63 db 78 4b fd e3 15  4b ff ff 6c 3c 5f 00 09  |.c.xK...K..l<_..|
00000150  7d 63 5b 78 38 42 a5 9c  81 22 00 24 7d 2c 4b 78  |}c[x8B...".$},Kx|
00000160  7d 29 03 a6 4e 80 04 21  3c 00 cc cc 81 7e 00 14  |})..N..!<....~..|
00000170  60 00 cc cd 7c 63 00 16  54 62 d9 7e 4b ff ff 78  |`...|c..Tb.~K..x|
00000180  38 00 00 00 90 1e 00 14  4b ff fe 70 38 21 00 80  |8.......K..p8!..|
00000190  80 01 00 08 81 61 00 04  ba e1 ff dc 7c 08 03 a6  |.....a......|...|
000001a0  7d 70 81 20 4e 80 00 20  bf 01 ff e0 7c 99 23 79  |}p. N.. ....|.#y|
000001b0  7c 08 02 a6 54 b8 06 3e  7c bb 2b 78 7c 7d 00 fe  ||...T..>|.+x|}..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 76 01 00 00  |............v...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



---

### Post by matt_symes on 2011-02-02
Hi

Well, i cannot see anything wrong with your boot setup from the script above (and that is a pain). If any else fancies casting their eyes over the script though that would be good.

Still there are some things you can try.

I would start by running a file system check on the drive from the LiveCD using GParted or fsck from the command line.

```
sudo fsck -y -V -f /dev/sda1
```

You could also try reinstalling grub.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You could also try rebuilding initramfs.

And, lastly, you could try reinstalling the kernel or an older kernel from a LiveCD.

Otherwise i am out of ideas.

Kind regards

---

### Post by CowboyBoats on 2011-02-10
I just tried reinstalling Ubuntu, and this time the installer crashed, leaving me with an unbootable drive. The Windows 7 install disk crashes too. Argh >.<

---

### Post by CowboyBoats on 2011-02-12
Maybe I just need a new hard drive? But the hard drive works fine for storing files, it seems weird to me that it could work perfectly and just not be able to install an operating system. Any advice?

---

### Post by matt_symes on 2011-02-14
Hi

Check the smart status of your drive. You can do that from the live CD.

Kind regards

---

