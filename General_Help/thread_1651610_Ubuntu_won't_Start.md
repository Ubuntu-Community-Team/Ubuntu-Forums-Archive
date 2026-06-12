---
title: "Ubuntu won't Start"
date: 2010-12-23
forum: General Help
---

### Post by saharasaidi on 2010-12-23
Ubuntu won't boot, just goes to a black screen. When I use a boot disk, it gives me this error message

(initramfs) /dev/loop0 (cdrom/caspev/filesyste/squashfs)

(this may not be completely correct)
What should I do?

---

### Post by karthick87 on 2010-12-23
Boot using a live cd and post the results of bootinfoscript with code(#) tags.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by amsterdamharu on 2010-12-23
Could be the disk is damaged or the DVD/CD drive has problems reading it. 

Is there an operating system installed on the computer you are trying to boot?
If so you might try unetbootin and just run the iso off the harddisk.

---

### Post by rvchari on 2010-12-23
```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000   7 HPFS/NTFS
/dev/sda2           3,074,048    48,580,607    45,506,560   7 HPFS/NTFS
/dev/sda3         467,914,752   488,394,751    20,480,000   7 HPFS/NTFS
/dev/sda4          48,595,741   467,903,519   419,307,779   5 Extended
/dev/sda5          48,595,743    97,403,039    48,807,297  83 Linux
/dev/sda6          97,403,103   126,705,599    29,302,497  83 Linux
/dev/sda7         126,705,663   224,365,679    97,660,017  83 Linux
/dev/sda8         224,365,743   322,023,711    97,657,969   7 HPFS/NTFS
/dev/sda9         322,025,823   458,740,799   136,714,977  83 Linux
/dev/sda10        458,740,863   467,903,519     9,162,657  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       4681a1a3-7a3a-44cb-b629-1eac3fe779b6   swap                                     
/dev/sda1        A24604274603FAB5                       ntfs       SERVICEV003                   
/dev/sda2        38981A009819BCF6                       ntfs                                     
/dev/sda3        2652087E520854C9                       ntfs       Lenovo                        
/dev/sda4: PTTYPE="dos" 
/dev/sda5        bcd52018-9be8-418c-91d1-d03f6a48789a   ext3                                     
/dev/sda6        34637be1-349c-4208-bd7d-6e5442d900a1   ext3                                     
/dev/sda7        202d6fdd-bfb8-4423-b08e-a93d7b2d2376   ext3       linux                         
/dev/sda8        06079E2E33F13F9B                       ntfs       windows                       
/dev/sda9        de3a7712-a05f-4242-ace6-d558f1668626   ext3       LinuxBackup                   
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
search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=bcd52018-9be8-418c-91d1-d03f6a48789a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=bcd52018-9be8-418c-91d1-d03f6a48789a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a24604274603fab5
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
UUID=bcd52018-9be8-418c-91d1-d03f6a48789a /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=34637be1-349c-4208-bd7d-6e5442d900a1 /home           ext3    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=4681a1a3-7a3a-44cb-b629-1eac3fe779b6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  35.7GB: boot/grub/core.img
  35.6GB: boot/grub/grub.cfg
  35.7GB: boot/initrd.img-2.6.35-23-generic
  33.6GB: boot/vmlinuz-2.6.35-23-generic
  35.7GB: initrd.img
  33.6GB: vmlinuz

---

### Post by rvchari on 2010-12-23
sorry for interruption karthik, infact i too m facing the same prob with a difference.
here i have posted in ur thread as i m yet to get reply there.... hope u wont mind and amster... will learn something from my boot info ?

---

### Post by karthick87 on 2010-12-23
[@rvchari]("http://ubuntuforums.org/member.php?u=1168146") What's your problem?Better you can open a new thread and explain your problem there.So that you can get answers quickly.

---

