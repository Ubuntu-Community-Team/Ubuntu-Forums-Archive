---
title: "Accessing Grub boot options..."
date: 2010-02-25
forum: General Help
---

### Post by jblaven on 2010-02-25
Hey guys,

Is there a way to access the list of boot options from Ubuntu?  I don't want to change the options, just have someone access the information, then copy and paste it in an email so I can see what the heck is going on with their computer.

The problem is this:

User has 2 physical drives.

Drive 1 has XP
Drive 2 has another version of XP on it as well as Ubuntu.

We want the computer to have the option to boot into XP on Drive 1 and Ubuntu on Drive 2.  Booting into XP on Drive 2 is an option.

We can get into Ubuntu, and XP on the 2nd Drive, but not XP on the 1st drive.

What other info should I gather?

Thanks,

Joe

---

### Post by oldfred on 2010-02-25
If you want to know about a boot process this script works great. If I am making changes to my system I run it before & after to make sure I know what is where. Run it on your system to see, it is long but includes much more info and just running a few commands.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

If you installed windows together it may have combined boots. I know it does on one drive, but not sure about 2 drives.
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by jblaven on 2010-02-25
Now that's just cool.  I ran the script on my computer and it worked like a charm.  Now all I have to do is run it on the other one.

Thanks!

---

### Post by jblaven on 2010-03-01
OK,

Here is the output...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=2d0e4aa7-9652-4241-828e-efa3bae2b232)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c879c87

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc9a0c9a0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    76,758,569    76,758,507  83 Linux
/dev/sdb2          76,758,570    78,172,289     1,413,720   5 Extended
/dev/sdb5          76,758,633    78,172,289     1,413,657  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A4443B40443B1490                       ntfs                                     
/dev/sdb1        2d0e4aa7-9652-4241-828e-efa3bae2b232   ext4                                     
/dev/sdb5        47ea9ea4-0cef-4f54-9354-f00c6adc06e3   swap                                     
/dev/sdc1        5810-51F2                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/5810-51F2         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 2d0e4aa7-9652-4241-828e-efa3bae2b232
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2d0e4aa7-9652-4241-828e-efa3bae2b232
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2d0e4aa7-9652-4241-828e-efa3bae2b232 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2d0e4aa7-9652-4241-828e-efa3bae2b232
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2d0e4aa7-9652-4241-828e-efa3bae2b232 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a4443b40443b1490
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=2d0e4aa7-9652-4241-828e-efa3bae2b232 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=47ea9ea4-0cef-4f54-9354-f00c6adc06e3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   3.3GB: boot/grub/core.img
   3.3GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: initrd.img
    .5GB: vmlinuz
```

---

### Post by oldfred on 2010-03-01
I do not see a copy of windows on sdb??

You do have the boot loaders on opposite drives from the operating systems. I prefer to have them on the same drive (so each drive could boot on its own) but it is not essential.

---

### Post by jblaven on 2010-03-01
Hey oldfred,

I decided to take Dad's computer home with me to work on...  I was under a time crunch, and that's always bad news when working on computers! :lolflag:

I didn't want to make a hasty mistake and delete any of his files.  I left him with a laptop till I can get his desktop up and running again.

I might need some help in how to do a search and pull all of his .doc files and .xls files from the computer so I can back them up.  I would like to do this from linux, but am unsure.  I tried to do a *.doc search from the gui, but it didn't like that!

---

### Post by oldfred on 2010-03-02
There seems to be two ways to search. If you want to search entire system I use places, search for files and choose filesystem. It sometimes takes a while.
When you open search from an open Nautilus screen, it seems to be a local search.

---

