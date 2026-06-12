---
title: "Grub not loading"
date: 2010-04-17
forum: General Help
---

### Post by polardude1983 on 2010-04-17
Ok so i have to hard drives sda and sdb.

My linux partition that i always used is on /dev/sda1

I keep trying to restore grub and it says its sucessfull but then there is no grub.

Now when i have the live cd in and i say install ubuntu 9.10 again It says there are no operating systems on this disc sdb

Which i thought was weird that it chose sdb and not my usual one sda.

So somehow my sdb hard disc is now my main drive? How do i get back my sda as my main

---

### Post by oldfred on 2010-04-17
Did you change boot order in BIOS, or physically change connections for sda & sdb?

If you want to see your entire configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by polardude1983 on 2010-04-17
no never physically changed the connections. all i did was format my sdb drive

---

### Post by jdackle on 2010-04-17
Did you check your BIOS settings?

---

### Post by polardude1983 on 2010-04-17
If i were to check the bios settings what would I be looking for?

---

### Post by wilee-nilee on 2010-04-17
> **polardude1983 said:**
> If i were to check the bios settings what would I be looking for?

I would follow oldfreds advice with the bootlaoder script. oldfred is very good at this sort of thing and will probably get you up and running. There are several other regulars on the forum who help people on these sort of matters and he is in the top-3 that I see regularly.

---

### Post by polardude1983 on 2010-04-17
K. I downloaded the bootloader script and will run it when i get back home.

---

### Post by polardude1983 on 2010-04-17
here is the info from the boot script

----------------------------------------------------------------
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   530,916,119   530,916,057  83 Linux
/dev/sda2    *    530,916,120   613,072,529    82,156,410   7 HPFS/NTFS
/dev/sda3         613,072,530   625,137,344    12,064,815   5 Extended
/dev/sda5         613,072,593   625,137,344    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ea90e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6876c9c2-22b4-42ee-9eff-0a2f61a305af   ext4                                     
/dev/sda2        7468B46768B42A2E                       ntfs                                     
/dev/sda5        726999da-9ea3-48d1-acd0-9cfc0e40fae5   swap                                     
/dev/sdb1        5d3a56c5-3254-4a23-938e-c498929a658a   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 7468b46768b42a2e
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Acronis Secure Zone (on /dev/sdb6)" {
    insmod fat
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set e61e-301c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 1799a3d2-6ecd-4a10-b25f-dffc6c9b5678
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1799a3d2-6ecd-4a10-b25f-dffc6c9b5678 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 1799a3d2-6ecd-4a10-b25f-dffc6c9b5678
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1799a3d2-6ecd-4a10-b25f-dffc6c9b5678 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sdb9) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set 40241da4-3779-41da-9250-e4b6480f6bec
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=40241da4-3779-41da-9250-e4b6480f6bec ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set 40241da4-3779-41da-9250-e4b6480f6bec
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=40241da4-3779-41da-9250-e4b6480f6bec ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=726999da-9ea3-48d1-acd0-9cfc0e40fae5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  37.8GB: boot/grub/core.img
  35.7GB: boot/grub/grub.cfg
    .2GB: boot/grub/stage2
   3.9GB: boot/initrd.img-2.6.31-14-generic
  44.9GB: boot/initrd.img-2.6.31-16-generic
  72.0GB: boot/initrd.img-2.6.31-17-generic
  72.4GB: boot/initrd.img-2.6.31-19-generic
  19.4GB: boot/initrd.img-2.6.31-20-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   2.5GB: boot/vmlinuz-2.6.31-16-generic
  42.4GB: boot/vmlinuz-2.6.31-17-generic
  69.8GB: boot/vmlinuz-2.6.31-19-generic
  15.1GB: boot/vmlinuz-2.6.31-20-generic
  37.8GB: grub/core.img
  19.4GB: initrd.img
  72.4GB: initrd.img.old
  15.1GB: vmlinuz
  69.8GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
```

---

### Post by polardude1983 on 2010-04-17
bump.

---

### Post by wilee-nilee on 2010-04-17
I think your on your way to resolution, I notice that sda2 is set as the boot, this may be part of the problem. I am not sure though lets wait for the local experts. Just commenting for a free bump. ;)

---

### Post by polardude1983 on 2010-04-17
can you bump just to bump?

---

### Post by ranch hand on 2010-04-17
Bumping more than once a day is not encouraged.

I am sure that oldfred will be back as his time allows.

If I can get the other thread I am working on straitened out I will have a look at this.

Here is a link that might give you some info;

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by polardude1983 on 2010-04-18
k

---

### Post by polardude1983 on 2010-04-18
Here is an update of the boot info

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   530,916,119   530,916,057  83 Linux
/dev/sda2         530,916,120   613,072,529    82,156,410   7 HPFS/NTFS
/dev/sda3         613,072,530   625,137,344    12,064,815   5 Extended
/dev/sda5         613,072,593   625,137,344    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ea90e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   522,112,499   522,112,437  83 Linux
/dev/sdb2         522,112,500   976,768,064   454,655,565  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6876c9c2-22b4-42ee-9eff-0a2f61a305af   ext4                                     
/dev/sda2        7468B46768B42A2E                       ntfs       Windows                       
/dev/sda5        726999da-9ea3-48d1-acd0-9cfc0e40fae5   swap                                     
/dev/sdb1        5d3a56c5-3254-4a23-938e-c498929a658a   ext3       Backup                        
/dev/sdb2        4918d811-79f5-4355-98e2-cca5ab1174ae   ext3       Extra Hard Drive              

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6876c9c2-22b4-42ee-9eff-0a2f61a305af
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 7468b46768b42a2e
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Acronis Secure Zone (on /dev/sdb6)" {
    insmod fat
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set e61e-301c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 1799a3d2-6ecd-4a10-b25f-dffc6c9b5678
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1799a3d2-6ecd-4a10-b25f-dffc6c9b5678 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 1799a3d2-6ecd-4a10-b25f-dffc6c9b5678
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1799a3d2-6ecd-4a10-b25f-dffc6c9b5678 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sdb9) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set 40241da4-3779-41da-9250-e4b6480f6bec
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=40241da4-3779-41da-9250-e4b6480f6bec ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set 40241da4-3779-41da-9250-e4b6480f6bec
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=40241da4-3779-41da-9250-e4b6480f6bec ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=726999da-9ea3-48d1-acd0-9cfc0e40fae5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  37.8GB: boot/grub/core.img
  35.7GB: boot/grub/grub.cfg
    .2GB: boot/grub/stage2
   3.9GB: boot/initrd.img-2.6.31-14-generic
  44.9GB: boot/initrd.img-2.6.31-16-generic
  72.0GB: boot/initrd.img-2.6.31-17-generic
  72.4GB: boot/initrd.img-2.6.31-19-generic
  19.4GB: boot/initrd.img-2.6.31-20-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   2.5GB: boot/vmlinuz-2.6.31-16-generic
  42.4GB: boot/vmlinuz-2.6.31-17-generic
  69.8GB: boot/vmlinuz-2.6.31-19-generic
  15.1GB: boot/vmlinuz-2.6.31-20-generic
  37.8GB: grub/core.img
  19.4GB: initrd.img
  72.4GB: initrd.img.old
  15.1GB: vmlinuz
  69.8GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
```

---

### Post by ed-koala on 2010-04-18
sda2 having the boot flag shouldn't be the problem.  Windows requires the boot flag to boot, Ubuntu/grub doesn't use it.

sdb just looks like a data drive to me, no operating system is installed on it. Is that correct?

Maybe you have Bios set to boot the wrong hard drive first?  Everything else looks ok to me, but I just might not have enough knowledge to spot a problem.

Oh, and you are using grub legacy, not grub2, just fyi.

---

### Post by ranch hand on 2010-04-18
That is your whole boot info script result?

Doesn't Mint have a boot loader?

Was this 9.10 a clean install or an upgrade from 9.04?

---

### Post by polardude1983 on 2010-04-18
No not a clean install of a OS. All i did was format my second hard drive and all of the sudden I can't load my ubuntu 9.10 OS

My ubuntu is on sda1 and its no longer booting at startup. For some reason my pc is trying to boot from the second hard drive and not the first.

---

### Post by john newbuntu on 2010-04-18
Get to your bios first.  Hit the F2 or F8 or delete or whatever key is shown on the first screen when you turn on your computer to get to the BIOS.  Then look at the order of booting of disks.  That should point to disk1.  If so you are ok. Exit.  Otherwise, switch the order.  Make disk1 first, SAVE and exit.

Edit: [http://www.whitecanyon.com/how-to-change-boot-order.php](http://www.whitecanyon.com/how-to-change-boot-order.php) is an example

---

### Post by polardude1983 on 2010-04-18
Ok well i checked the boot order and it was sata 4 then sata 1 and i switched it

But now when i start up it loads up into a command line grub

it shows just a black screen and this 'grub>'

---

### Post by john newbuntu on 2010-04-18
First part solved.  Now follow "[FONT=Arial][SIZE=1][COLOR=red]How to restore the Ubuntu grub bootloader (9.04 and older)[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1]"[/SIZE][/FONT]
from [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by polardude1983 on 2010-04-18
here is what i get from the terminal

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33048   265458028+  83  Linux
/dev/sda2           33049       38162    41078205    7  HPFS/NTFS
/dev/sda3           38163       38913     6032407+   5  Extended
/dev/sda5           38163       38913     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       32500   261056218+  83  Linux
/dev/sdb2           32501       60801   227327782+  83  Linux
ubuntu@ubuntu:~$ sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mkdir /media/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda1 /dev/sda
Installation finished. No error reported.
This is the contents of the device map /media/sda1/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

```

---

### Post by polardude1983 on 2010-04-18
also from terminal

ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$

---

### Post by ranch hand on 2010-04-18
Well that explains the lack of information on Mint.

It does not explain how Ubuntu 9.10 was installed.  The boot info script results clearly states that grub0.97 is installed on your MBR of sda.   Then we get the output from the grub.cfg file.  This is very interesting as grub0.97 does not have a grub.cfg file.

The default grub for Ubuntu 9.10 is grub1.97beta4.

A little information on your installation is really, just maybe, important.

---

### Post by ranch hand on 2010-04-18
> **polardude1983 said:**
> also from terminal

ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$
If you are running that command you need to be on CD from 9.04 or earlier where grub0.97 is installed.

A 9.10 disk has no idea what you are talking about aany more that a 9.04 disk is going to understand about grub1.9xxx.

---

### Post by john newbuntu on 2010-04-18
What you had was the legacy grub and should have run from liveCD:

sudo grub
find /boot/grub/stage1
root (hd0,1)
setup (hd0)

---

### Post by polardude1983 on 2010-04-18
> **ranch hand said:**
> Well that explains the lack of information on Mint.

It does not explain how Ubuntu 9.10 was installed.  The boot info script results clearly states that grub0.97 is installed on your MBR of sda.   Then we get the output from the grub.cfg file.  This is very interesting as grub0.97 does not have a grub.cfg file.

The default grub for Ubuntu 9.10 is grub1.97beta4.

A little information on your installation is really, just maybe, important.

Thats because i use ubuntu 9.10. And i'm currently using the 9.10 live cd. so what do i need to do. I'm trying to get back to my ubuntu 9.10 on my hard drive

---

### Post by polardude1983 on 2010-04-18
Wait so i have to usea  9.04 ubuntu live cd to restore my grub so i can get back to my 9.10 ubuntu operating system?

---

### Post by ranch hand on 2010-04-18
It might work but your boot info script has the grub.cfg output which is not part of grub0.97 which is what 9.04 would understand.

---

### Post by john newbuntu on 2010-04-18
[B][SIZE=2]Follow the steps "Uninstalling GRUB 2" from [/SIZE]
[/B]

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Ranch hand  has definitely more experience when it comes to restoring legacy grub.  Take a second opinion from him and see if grub.cfg needs to be moved out of the way after mounting your boot partition.  Thanks in advance Ranch Hand.

---

### Post by polardude1983 on 2010-04-18
> **john newbuntu said:**
> [B][SIZE=2]Follow the steps "Uninstalling GRUB 2" from [/SIZE]
[/B]

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Ranch hand  has definitely more experience when it comes to restoring legacy grub.  Take a second opinion from him and see if grub.cfg needs to be moved out of the way after mounting your boot partition.  Thanks in advance Ranch Hand.

alright i will try this

---

### Post by polardude1983 on 2010-04-18
when i get to this point of the uninstalling grub 2

sudo grub-install /dev/sda

I get this from the terminal

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$

---

### Post by ranch hand on 2010-04-18
I would still like to know that this is really an upgrade or if it was a clean install that has, somehow, gotten corrupted.

We have conflicting evidence of what grub is installed.

Has;
```

grub-install -v

```
been run?

That just gives the version number that your box thinks it is running.

---

### Post by polardude1983 on 2010-04-18
ubuntu@ubuntu:~$ grub-install -v
grub-install (GNU GRUB 0.97)
ubuntu@ubuntu:~$

---

### Post by polardude1983 on 2010-04-18
So i need to use a 9.04 ubuntu disc now?

---

### Post by oldfred on 2010-04-18
I am not sure what you have done so far. If you have totally install grub legacy ignore this.
The boot script shows grub2 installed in your partition but grub legacy (0.97) in the MBR.

These are all grub2 files:
Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img
Grub 0.97 is installed in the MBR of /dev/sda

While with Karmic new installs were grub2, but upgrades were grub legacy now we will with lucid get even more grub2 installs and those with older versions will still have old grub. Those users looking on the internet will find instructions to reinstall grub (old grub) and not realize they may have grub2 and the instructions are different. In fact having both installed creates even more issues.

To reinstall grub2 to the MBR (assuming you still have the grub2 files in your sda1.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

reinstall from live cd 
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by ranch hand on 2010-04-18
Well, yes I would give that a try.  I still think you have combined install and the only way to know that is for you to tell us if 9.10 was a clean install or an upgrade from 9.04.

This is not a difficult question.

If it is an upgrade we need to deal with this in a different manner.

---

### Post by polardude1983 on 2010-04-18
This is what i got from the following commands

```
ubuntu@ubuntu:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
mount: /dev/sda1 already mounted or /media/sda1 busy
mount: according to mtab, /dev/sda1 is already mounted on /media/sda1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda1 /dev/sda
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /media/sda1/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$ 

```

---

### Post by ed-koala on 2010-04-18
There might be an easier way, taking advantage of Windows' desire to crowd out everything else.

Since you are dual booting, if you just uninstall grub legacy and grub2 (to be safe), then use a windows disk to "fix" the MBR, it'll wipe the MBR for you pretty well, then you can fresh install Grub2 from the 9.10 CD.

That should work, though you may have to edit a file after to get everything appearing as you'd like it, but that's the easiest part.

Just throwing this out as an idea. I'd like a second opinion before trying it.

---

### Post by polardude1983 on 2010-04-18
> **ranch hand said:**
> Well, yes I would give that a try.  I still think you have combined install and the only way to know that is for you to tell us if 9.10 was a clean install or an upgrade from 9.04.

This is not a difficult question.

If it is an upgrade we need to deal with this in a different manner.

no it was a clean install never had ubuntu 9.04

---

### Post by polardude1983 on 2010-04-18
> **oldfred said:**
> I am not sure what you have done so far. If you have totally install grub legacy ignore this.
The boot script shows grub2 installed in your partition but grub legacy (0.97) in the MBR.

These are all grub2 files:
Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img
Grub 0.97 is installed in the MBR of /dev/sda

While with Karmic new installs were grub2, but upgrades were grub legacy now we will with lucid get even more grub2 installs and those with older versions will still have old grub. Those users looking on the internet will find instructions to reinstall grub (old grub) and not realize they may have grub2 and the instructions are different. In fact having both installed creates even more issues.

To reinstall grub2 to the MBR (assuming you still have the grub2 files in your sda1.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

reinstall from live cd 
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

still having the problem and it still doesn't work

---

### Post by polardude1983 on 2010-04-19
ok so i got the 9.10 live cd in and did this

ubuntu@ubuntu:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
ubuntu@ubuntu:~$ 

should i uninstall that too?

---

### Post by polardude1983 on 2010-04-19
Frikin finally I got it!!!! I dont know what i did. but i did it.

You all are the best.

---

