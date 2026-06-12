---
title: "how to recover data form ubuntu 11.04"
date: 2011-10-10
forum: General Help
---

### Post by spkanu on 2011-10-10
i have just lost my all partition and data when i installed ubuntu 11.04.
can you tell me how i will get this data and do the patition again.

---

### Post by Rubi1200 on 2011-10-11
Hi and welcome to the forums :-)

Please tell us exactly what happened.

Did you choose the option to "erase and use entire disk"?

Stop any activity on the disk now as any read/write activity can make recovery even more difficult.

Which operating system was on the computer before this happened?

Did you make backups before installing 11.04?

The more you tell us, the better.

---

### Post by mikejonesey on 2011-10-11
this will be difficult as it will be hard to know where the partitions began and ended, your best bet is to use a tool attempt to cipher where the partitions started and ended and then write these partition tables back... you will the copy the data by mounting the partitions via a third party like a liveCD or USB or another hdd...

Important:
do not write or boot this disk untill you have your files... (this corrupts old data by overwriting it...)

the best tool i'm aware of to ciper where partitions were is... **testdisk**

the best tool i'm aware of to write partition tables is **fdisk**

i've used these tools many times and have restored entire partitions even after a few months of use on another partition base... (after fixing a few things)... regardless you should never write to the disk (except to restore a partition table), until you have your data back...

---

### Post by spkanu on 2011-10-11
it was win 7 64bit.
and it does't say to earas it.
i have installed ubuntu with live cd

---

### Post by Rubi1200 on 2011-10-11
I suggest you post the results of the boot info script so we can see what is going on.

There is a link at the bottom of my post with instructions.

---

### Post by spkanu on 2011-10-11
i have found my lost data by testdisk....
thank you..
but now i have encounter one more problem that when i boot my computer it will show the blank screen n in that
grub rescue>
this command promt will appear. so i couldn't get to access my syatem
could u please help me out

---

### Post by Rubi1200 on 2011-10-12
Please post the results of the boot info script (as I suggested before).

---

### Post by spkanu on 2011-10-12
i got my data back from testdisk...
but now i have encounter one another problem of booting.
that it will not boot and says
no partition find
grub rescue>

---

### Post by coffeecat on 2011-10-12
@spkanu, **please** run the boot info script as Rubi1200 suggested. No one can help you without that information.

---

### Post by spkanu on 2011-10-12
boot script info

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 84195552 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos2)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1          92,164,966   488,392,064   396,227,099   f W95 Extended (LBA)
/dev/sda5          92,164,968   296,961,524   204,796,557   7 NTFS / exFAT / HPFS
/dev/sda6         296,961,588   488,392,064   191,430,477   7 NTFS / exFAT / HPFS
/dev/sda2    *          2,048    92,164,095    92,162,048  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        82beb0a6-63fb-4969-9c31-1a11fd379999   ext4       
/dev/sda5        821008AE1008AAED                       ntfs       New Volume
/dev/sda6        4000B10800B105C6                       ntfs       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 82beb0a6-63fb-4969-9c31-1a11fd379999
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 82beb0a6-63fb-4969-9c31-1a11fd379999
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 82beb0a6-63fb-4969-9c31-1a11fd379999
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=82beb0a6-63fb-4969-9c31-1a11fd379999 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 82beb0a6-63fb-4969-9c31-1a11fd379999
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=82beb0a6-63fb-4969-9c31-1a11fd379999 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 82beb0a6-63fb-4969-9c31-1a11fd379999
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 82beb0a6-63fb-4969-9c31-1a11fd379999
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=82beb0a6-63fb-4969-9c31-1a11fd379999 /               ext4    errors=remount-ro 0       1
# /dos was on /dev/sda6 during installation
UUID=4000B10800B105C6 /dos            ntfs    defaults,umask=007,gid=46 0       0
# /windows was on /dev/sda5 during installation
UUID=821008AE1008AAED /windows        ntfs    defaults,umask=007,gid=46 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  40.147594452 = 43.108151296   boot/grub/core.img                             1
  40.147605896 = 43.108163584   boot/grub/grub.cfg                             1
   4.380104065 = 4.703100928    boot/initrd.img-2.6.38-8-generic               2
  40.145866394 = 43.106295808   boot/vmlinuz-2.6.38-8-generic                  1
   4.380104065 = 4.703100928    initrd.img                                     2
  40.145866394 = 43.106295808   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
```

---

### Post by Elfy on 2011-10-12
Thread closed. Please do not post duplicates, it dilutes community effort.

You are getting help in the other thread about the booting issue.

---

