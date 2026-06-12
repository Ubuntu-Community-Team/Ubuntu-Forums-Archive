---
title: "Windows 7 and Ubuntu 10.10 --Virus"
date: 2010-12-23
forum: General Help
---

### Post by Sharpiedeluxe on 2010-12-23
So, this problem has really been getting at me, I can't figure it out at all. About a week ago, I came home from school and found that my computer was shut down (usually I leave it on), I started it up in Windows 7 and a Malware Bytes scan said it found a virus "clipb.exe". Well, I decided to remove it, and when booting up in windows it BSOD's saying IRQL_NOT_LESS_OR_EQUAL immediately at the login screen. Same result in safe mode and "last known configuration". Well, I decided to reformat just because I didn't want to go through too much trouble, and about a week later (today) it came back. I have no clue how, I was away from my computer. But the difference between this time and last time is, I can't start ubuntu at all. period. It gets to grub, and then after that gets to a black screen with no progress. The only thing I can do is ctrl+alt+dlt which restarts the computer. Has anyone else had an issue like this?

---

### Post by Rubi1200 on 2010-12-23
I highly recommend you check if your RAM is still in order.

From an Ubuntu LiveCD, pick the option to check memory. Let it run, it can take quite some time, and see what the results are.

You may need to clean/replace the memory sticks.

The Ubuntu issues sounds as if it might be graphics related; what card is installed?

---

### Post by Sharpiedeluxe on 2010-12-23
Okay, I probably should've added that. I did do a memtest, and it didn't show any errors.

---

### Post by wilee-nilee on 2010-12-23
Are you using the computer in admin rather then a limited account, and do you have a strong password and is it different then the one before the reinstall.

---

### Post by Sharpiedeluxe on 2010-12-23
I found that I can start ubuntu in recovery mode, but it drops me to a shell saying that /dev/disk/by-uuid/.../ does not exist. I have Windows 7 and Ubuntu 10.10 on the same drive but different partitions. Is it possible that a BSOD can lock the drive?

---

### Post by sikander3786 on 2010-12-23
> but it drops me to a shell saying that /dev/disk/by-uuid/.../ does not exist.

Can't it be a problem with you HDD?

Please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by Sharpiedeluxe on 2010-12-23
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 172068521 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   164,409,209   164,409,147   7 HPFS/NTFS
/dev/sda2         164,409,210   168,505,784     4,096,575  82 Linux swap / Solaris
/dev/sda3         168,505,785   207,575,864    39,070,080  83 Linux
/dev/sda4         207,575,865   312,576,704   105,000,840  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   390,716,864   390,716,802   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0242BBD542BBCBA3                       ntfs                                     
/dev/sda2        503f2012-2b54-4f50-97db-489a04817d15   swap                                     
/dev/sda3        de56af6e-c70d-482b-8e33-a4e9212fd477   reiserfs                                 
/dev/sda4        a8a752ba-038a-4c51-aa25-2c64719ec449   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        479D15A376C433A1                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
insmod reiserfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set de56af6e-c70d-482b-8e33-a4e9212fd477
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod reiserfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set de56af6e-c70d-482b-8e33-a4e9212fd477
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
    insmod reiserfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set de56af6e-c70d-482b-8e33-a4e9212fd477
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=de56af6e-c70d-482b-8e33-a4e9212fd477 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod reiserfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set de56af6e-c70d-482b-8e33-a4e9212fd477
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=de56af6e-c70d-482b-8e33-a4e9212fd477 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod reiserfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set de56af6e-c70d-482b-8e33-a4e9212fd477
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=de56af6e-c70d-482b-8e33-a4e9212fd477 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod reiserfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set de56af6e-c70d-482b-8e33-a4e9212fd477
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=de56af6e-c70d-482b-8e33-a4e9212fd477 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod reiserfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set de56af6e-c70d-482b-8e33-a4e9212fd477
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod reiserfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set de56af6e-c70d-482b-8e33-a4e9212fd477
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0242bbd542bbcba3
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=de56af6e-c70d-482b-8e33-a4e9212fd477 /               reiserfs notail          0       1
# /home was on /dev/sda4 during installation
UUID=a8a752ba-038a-4c51-aa25-2c64719ec449 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=503f2012-2b54-4f50-97db-489a04817d15 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg
    ??GB: boot/initrd.img-2.6.35-22-generic
    ??GB: boot/initrd.img-2.6.35-24-generic
    ??GB: boot/vmlinuz-2.6.35-22-generic
    ??GB: boot/vmlinuz-2.6.35-24-generic
    ??GB: initrd.img
    ??GB: initrd.img.old
    ??GB: vmlinuz
    ??GB: vmlinuz.old
```

Looks okay, to me though..let me know if you see something strange please

---

### Post by wilee-nilee on 2010-12-23
** Grub 0.97** is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #3 for /boot/grub/stage2 and **/boot/grub/menu.lst.**

This is grub-legacy, seems to be only in the mbr at this point. Boot a 10.10 live Ubuntu cd only a 10.10 and run these two commands.
```
sudo mount /dev/sda3 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot hopefully to the grub menu choose the Ubuntu install when in in the terminal run.
```
sudo update-grub
```

---

### Post by Sharpiedeluxe on 2010-12-23
```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

Gave me this error, but I can boot into ubuntu now! :D
Thank you so much! I should try updating grub now.

Well, that solves the ubuntu issue..at least I have a working OS, but Windows 7 on the other hand. KlamAV scan couldn't find anything.

---

### Post by Rubi1200 on 2010-12-23
You mentioned MalwareBytes in your first post. 

Were you also running other AV software; Avast perhaps?

---

