---
title: "GRUB 2.0 wont boot from external HDD with 2 systems installed on it."
date: 2011-09-03
forum: General Help
---

### Post by smile4max on 2011-09-03
I have a:
- laptop with installed Ubuntu 11.04 (disk1)
- PC with installed Ubuntu 11.04 and Windows XP (disk2) 

I've connected disk2 to the laptop (external USB) and tried to configure GRUB with instructions from different forums and sites. 
The only progress that I've made is that now GRUB is seeing all the installed systems but cannot boot to those that are installed on the external (disk2). 
When choosing Ubuntu 11.04 or XP from the disk2 GRUB gets stuck and nothing happens.

The external disk (disk2) has all the database and information that I need so cant risk with formatting and so on to avoid data loss.

May you please try help me out? cant do it by my self and cannot google the right answer.
its very important to me.

---

### Post by dino99 on 2011-09-03
scroll down the page: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by smile4max on 2011-09-03
Thank you for the answer but I've been to this page a lot of times but just given up. Cant find the right information. As I said before, I've googled the problem and have been surfing the net for week. That's why am lookinf for help.

Posting the sudo fdisk -l here. Some body may find this info. helpful:
**********************
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005de94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37841   303949824   83  Linux
/dev/sda2           37841       38914     8619009    5  Extended
/dev/sda5           37841       38914     8619008   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001aceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       53650   430943593+  83  Linux
/dev/sdb2   *       53651       60145    52171087+   7  HPFS/NTFS
/dev/sdb3           60146       60802     5264385    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sdb5           60146       60802     5264384   82  Linux swap / Solaris

**********************

---

### Post by garvinrick4 on 2011-09-03
Anything would be a quess without posting a bootscript here:
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 
Download this .zip file to DESKTOP copy and paste directions below one at a time in a terminal.
```
cd Desktop
``````
ls
``````
 unzip boot_info_script060.zip
``` ```
 chmod +x  boot_info_script.sh
``````
 sudo ./boot_info_script.sh
```Will now have a RESULTS text file on Desktop copy and paste here.
Highlight whole thing after pasted to your message box and hit the # sign in upper right
will put it nice code tags and be easier to read.

---

### Post by smile4max on 2011-09-03
O.k. Done

The result:
**********

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   607,901,695   607,899,648  83 Linux
/dev/sda2         607,903,742   625,141,759    17,238,018   5 Extended
/dev/sda5         607,903,744   625,141,759    17,238,016  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   861,887,249   861,887,187  83 Linux
/dev/sdb2    *    861,887,250   966,229,424   104,342,175   7 NTFS / exFAT / HPFS
/dev/sdb3         966,244,350   976,773,119    10,528,770   5 Extended
/dev/sdb5         966,244,352   976,773,119    10,528,768  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        f321a25a-c567-41b3-98c2-8408d58c086e   ext4       
/dev/sda5        7a211cfe-11f0-4f45-8fdb-05ee369ebcd8   swap       
/dev/sdb1        7bee809b-8b1d-4a04-a47a-52abbc3a6ad4   ext4       
/dev/sdb2        7A10EC7410EC3931                       ntfs       
/dev/sdb5        92fa2ba9-3f26-4d5d-a560-bf3ef5af42af   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb2        /media/7A10EC7410EC3931  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
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
menuentry 'Ubuntu, with Linux 3.0.0-0300-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux    /boot/vmlinuz-3.0.0-0300-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-0300-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-0300-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    echo    'Loading Linux 3.0.0-0300-generic ...'
    linux    /boot/vmlinuz-3.0.0-0300-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-0300-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro single
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 7A10EC7410EC3931
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
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
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.130104065 = 4.434665472    boot/grub/core.img                             1
 255.816497803 = 274.680872960  boot/grub/grub.cfg                             1
   7.259677887 = 7.795019776    boot/initrd.img-2.6.32-31-generic              2
   7.805664062 = 8.381267968    boot/initrd.img-2.6.35-28-generic              2
 253.778694153 = 272.492797952  boot/initrd.img-2.6.38-10-generic              2
 142.403869629 = 152.904990720  boot/initrd.img-2.6.38-11-generic              1
  15.637100220 = 16.790208512   boot/initrd.img-2.6.38-8-generic               2
 141.505828857 = 151.940726784  boot/initrd.img-3.0.0-0300-generic             2
   4.442256927 = 4.769837056    boot/vmlinuz-2.6.32-31-generic                 1
   4.403461456 = 4.728180736    boot/vmlinuz-2.6.35-28-generic                 1
 255.763008118 = 274.623438848  boot/vmlinuz-2.6.38-10-generic                 2
 141.692695618 = 152.141373440  boot/vmlinuz-2.6.38-11-generic                 1
   9.001285553 = 9.665056768    boot/vmlinuz-2.6.38-8-generic                  1
 141.368587494 = 151.793364992  boot/vmlinuz-3.0.0-0300-generic                2
 142.403869629 = 152.904990720  initrd.img                                     1
 141.505828857 = 151.940726784  initrd.img.old                                 2
 141.692695618 = 152.141373440  vmlinuz                                        1
 141.368587494 = 151.793364992  vmlinuz.old                                    2

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7bee809b-8b1d-4a04-a47a-52abbc3a6ad4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro single
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux /boot/vmlinuz-2.6.32-31-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root f321a25a-c567-41b3-98c2-8408d58c086e
    linux /boot/vmlinuz-2.6.32-31-generic root=UUID=f321a25a-c567-41b3-98c2-8408d58c086e ro single
    initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 7A10EC7410EC3931
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
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7bee809b-8b1d-4a04-a47a-52abbc3a6ad4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=92fa2ba9-3f26-4d5d-a560-bf3ef5af42af none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  98.129157543 = 105.365380608  boot/grub/core.img                             1
  98.129168987 = 105.365392896  boot/grub/grub.cfg                             1
 394.082942486 = 423.143337472  boot/initrd.img-2.6.35-28-generic              2
 370.433871746 = 397.750341120  boot/initrd.img-2.6.38-10-generic              2
 300.660438061 = 322.831687168  boot/initrd.img-2.6.38-8-generic               1
 104.053306103 = 111.726386688  boot/vmlinuz-2.6.35-28-generic                 1
 369.898776531 = 397.175787008  boot/vmlinuz-2.6.38-10-generic                 2
 100.058928967 = 107.437456896  boot/vmlinuz-2.6.38-8-generic                  1
 370.433871746 = 397.750341120  initrd.img                                     2
 300.660438061 = 322.831687168  initrd.img.old                                 1
 369.898776531 = 397.175787008  vmlinuz                                        2
 100.058928967 = 107.437456896  vmlinuz.old                                    1

================================ sdb2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error


```

---

### Post by Quackers on 2011-09-03
Is your laptop's bios configured to boot from a USB HDD? I have to enable that function on mine then I can put the option in the boot order.

---

