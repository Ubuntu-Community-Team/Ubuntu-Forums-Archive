---
title: "Grub2 won't boot Windows XP"
date: 2010-06-26
forum: General Help
---

### Post by snowmanman on 2010-06-26
Windows has some files I need and when I try to boot it hangs at a black screen with a blinking cursor.

I checked grub.cfg and this entry was in there:
```
## BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ae748d2b748cf77d
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

Any suggestions on how to boot?

---

### Post by warfacegod on 2010-06-26
Any reason you can't get them from inside Ubuntu? I know it's not a fix for XP not booting but for the moment...

---

### Post by snowmanman on 2010-06-26
Yeah, but what if I want to use a program that Ubuntu doesn't have, like Peerblock or some games I have.

---

### Post by warfacegod on 2010-06-26
Post the results of this: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

The info will help us to resolve your issue.

---

### Post by snowmanman on 2010-06-26
I hope you can make some sense out of all this :p.

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 40811687 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 40731431 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,355,279    40,355,217   7 HPFS/NTFS
/dev/sda2          40,355,280    78,124,094    37,768,815   5 Extended
/dev/sda5          40,355,343    76,453,334    36,097,992  83 Linux
/dev/sda6          76,453,398    78,124,094     1,670,697  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   160,826,714   160,826,652   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AE748D2B748CF77D                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        335ebc91-b36b-4e6a-9248-9f698b91a2d8   ext4                                     
/dev/sda6        6935e2c6-9ed0-46c9-870b-82727581e621   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        60949C6F949C4984                       ntfs       Storage                       
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/AE748D2B748CF77D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 335ebc91-b36b-4e6a-9248-9f698b91a2d8
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 335ebc91-b36b-4e6a-9248-9f698b91a2d8
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 335ebc91-b36b-4e6a-9248-9f698b91a2d8
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=335ebc91-b36b-4e6a-9248-9f698b91a2d8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 335ebc91-b36b-4e6a-9248-9f698b91a2d8
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=335ebc91-b36b-4e6a-9248-9f698b91a2d8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 335ebc91-b36b-4e6a-9248-9f698b91a2d8
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=335ebc91-b36b-4e6a-9248-9f698b91a2d8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 335ebc91-b36b-4e6a-9248-9f698b91a2d8
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=335ebc91-b36b-4e6a-9248-9f698b91a2d8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 335ebc91-b36b-4e6a-9248-9f698b91a2d8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 335ebc91-b36b-4e6a-9248-9f698b91a2d8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ae748d2b748cf77d
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=335ebc91-b36b-4e6a-9248-9f698b91a2d8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6935e2c6-9ed0-46c9-870b-82727581e621 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  20.8GB: boot/grub/core.img
  23.5GB: boot/grub/grub.cfg
  27.7GB: boot/initrd.img-2.6.31-21-generic
  28.2GB: boot/initrd.img-2.6.32-22-generic
  27.1GB: boot/vmlinuz-2.6.31-21-generic
  26.3GB: boot/vmlinuz-2.6.32-22-generic
  28.2GB: initrd.img
  27.7GB: initrd.img.old
  26.3GB: vmlinuz
  27.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by wilee-nilee on 2010-06-26
So you have grub in you main booting XP OS sda1 we want to get rid of that, so XP can be booted. Use this link just follow the instructions.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You also have grub in sb1 but this looks to be a data partition, and can be removed with this link as well or manually by finding the grub file, but I don't think the sdb1 is causing you any problems as it is not part of the booting mechanism, it has a boot flag on it though, so lets get rid of grub from sda1 to begin with.

---

### Post by snowmanman on 2010-06-26
> **wilee-nilee said:**
> So you have grub in you main booting XP OS sda1 we want to get rid of that, so XP can be booted. Use this link just follow the instructions.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You also have grub in sb1 but this looks to be a data partition, and can be removed with this link as well or manually by finding the grub file, but I don't think the sdb1 is causing you any problems as it is not part of the booting mechanism, it has a boot flag on it though, so lets get rid of grub from sda1 to begin with.


That worked perfectly thanks! Probably not going back there for awhile.

---

### Post by wilee-nilee on 2010-06-26
> **snowmanman said:**
> That worked perfectly thanks! Probably not going back there for awhile.

Great you just want to be aware that if you get a prompt to where to install grub it goes to the master boot record only which is sda on the first HD. Grub can be put in a partition but you have to know why your doing that for a custom setup.

---

### Post by warfacegod on 2010-06-26
Would it be safe to assume that the link you posted works for XP, Vista, and 7?

---

### Post by wilee-nilee on 2010-06-26
> **warfacegod said:**
> Would it be safe to assume that the link you posted works for XP, Vista, and 7?

Yes if grub is in the boot it works but the script shows a lot of other information that is important information, and so it can be a set of other problems. It is important to know what the stock boot files that are needed are for each of these MS setups, and if somebody has done a upgrade or used a 3rd part like easybcd to boot Ubuntu before the ext4 and grub2 changes, so it can be rather convoluted. I mainly try to just get the bootscript on the thread and If I don't see a fix I let the OP know this and that there are people who are very good at this and to hang for help. I think you probably know the core group who do this daily.

The script also can show messed up uuid's and at times it is just having the wrong HD in the boot order rather then the grub in MS. Hey I'm still learning this stuff, and am in the end just concerned first that I don't bork somebodies setup by giving out commands willy-nilly;)

---

