---
title: "After latest grub update - unable to access windows!!!!111"
date: 2010-06-20
forum: General Help
---

### Post by Vorian on 2010-06-20
After doing my weekly update, I discovered that I am not able to access Windows.  

My windows entry still shows in my grub list on the boot menu
The windows partition is still there

However, when I select windows as the os from the boot menu, i get a black screen with a white cursor in the top left corner.

Please help because I am very stupid and do not know much of linux.

---

### Post by wilee-nilee on 2010-06-20
Post the bootscipt in my signature in code tags if you can.;)

---

### Post by Vorian on 2010-06-20
```
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Computing Partition Table of /dev/sdc...
Computing Partition Table of /dev/sdd...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sdb1 for information... 
Searching sdc1 for information... 
Searching sdd1 for information... 
Finished. The results are in the file RESULTS.txt located in /home/steve/Downloads
steve@fancy-pants:~/Downloads$
```



*edit* windows is on SDB1

---

### Post by oldfred on 2010-06-20
ok the script ran fine and the results.txt is in your Downloads dir.

Copy, paste, highlight, and click on # (code tags) above as you paste to make it easier for us to read.

---

### Post by Vorian on 2010-06-21
```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 273663 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 278015 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 273663 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   937,167,839   937,167,777  83 Linux
/dev/sda2         937,167,840   976,768,064    39,600,225   5 Extended
/dev/sda5         937,167,903   976,768,064    39,600,162  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   390,719,487   390,717,440   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   976,769,023   976,766,976   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2063 MB, 2063597568 bytes
255 heads, 63 sectors/track, 250 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63     4,016,249     4,016,187   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8b2be84f-210e-4c42-9fdd-eef715de5564   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1e6d16b5-fb06-4f1c-94b7-18331503d5ea   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F4DA39EFDA39AF2C                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        5A1ACE831ACE5C1F                       ntfs       New Volume                    
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        84A1-9792                              vfat                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/F4DA39EFDA39AF2C  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/84A1-9792         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1001,gid=1001,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set 8b2be84f-210e-4c42-9fdd-eef715de5564
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
search --no-floppy --fs-uuid --set 8b2be84f-210e-4c42-9fdd-eef715de5564
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8b2be84f-210e-4c42-9fdd-eef715de5564
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=8b2be84f-210e-4c42-9fdd-eef715de5564 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8b2be84f-210e-4c42-9fdd-eef715de5564
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=8b2be84f-210e-4c42-9fdd-eef715de5564 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8b2be84f-210e-4c42-9fdd-eef715de5564
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8b2be84f-210e-4c42-9fdd-eef715de5564 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8b2be84f-210e-4c42-9fdd-eef715de5564
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8b2be84f-210e-4c42-9fdd-eef715de5564 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8b2be84f-210e-4c42-9fdd-eef715de5564
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=8b2be84f-210e-4c42-9fdd-eef715de5564 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8b2be84f-210e-4c42-9fdd-eef715de5564
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=8b2be84f-210e-4c42-9fdd-eef715de5564 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8b2be84f-210e-4c42-9fdd-eef715de5564
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8b2be84f-210e-4c42-9fdd-eef715de5564
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set f4da39efda39af2c
    chainloader +1
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
UUID=8b2be84f-210e-4c42-9fdd-eef715de5564 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1e6d16b5-fb06-4f1c-94b7-18331503d5ea none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
  92.8GB: boot/grub/grub.cfg
  70.9GB: boot/initrd.img-2.6.31-20-generic
  75.2GB: boot/initrd.img-2.6.32-21-generic
  73.0GB: boot/initrd.img-2.6.32-22-generic
  16.1GB: boot/vmlinuz-2.6.31-20-generic
  93.9GB: boot/vmlinuz-2.6.32-21-generic
 121.5GB: boot/vmlinuz-2.6.32-22-generic
  73.0GB: initrd.img
  75.2GB: initrd.img.old
 121.5GB: vmlinuz
  93.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh  
```

---

### Post by wilee-nilee on 2010-06-21
You got it hold on, and I will defer to oldfred here.;)

---

### Post by Vorian on 2010-06-21
The last line of my op was a lie, I'm just baffled at what happened to my boot menu.

I like your script too, very intuitive.

---

### Post by wilee-nilee on 2010-06-21
> **Vorian said:**
> The last line of my op was a lie, I'm just baffled at what happened to my boot menu.

I like your script too, very intuitive.

The script isn't mine I'm not that smart it has the name of the origin in my sig.

---

### Post by oldfred on 2010-06-21
When the instructions said all drives they meant sda, sdb etc not partitions sda1, sda2 sdb1 etc. You overwrote the windows boot sector in the windows partition - sdb1.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If this is from the upgrade and you were confused by the instructions please add to the bug list. The maintainers do not consider it a bug, but do promise a fix eventually.
Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)
[https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1](https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1)

---

