---
title: "ubuntu 12.04 boot option disappeared in grub menu"
date: 2012-05-05
forum: General Help
---

### Post by crazycc on 2012-05-05
After using grub customizer to hide some duplicated boot options, the ubuntu 12.04 boot option disappeared, now there are only 2 options remained, memtest and my windows 7 boot options. What do I need to do to start ubuntu again? What commands I need to input in the grub command line?

---

### Post by 2ta8gdfte on 2012-05-05
> **crazycc said:**
> After using grub customizer to hide some duplicated boot options, the ubuntu 12.04 boot option disappeared, now there are only 2 options remained, memtest and my windows 7 boot options. What do I need to do to start ubuntu again? What commands I need to input in the grub command line?

You might use supergrub to get in as the easiest approach to cleanup your work. I wouldn't repair with it but just to boot the Ubuntu. 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by crazycc on 2012-05-05
> **2ta8gdfte said:**
> You might use supergrub to get in as the easiest approach to cleanup your work. I wouldn't repair with it but just to boot the Ubuntu. 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Thanks for the information. I tried the super grub2 disk, but no luck. Do I have to reinstall ubuntu again?

---

### Post by 2ta8gdfte on 2012-05-05
> **crazycc said:**
> Thanks for the information. I tried the super grub2 disk, but no luck. Do I have to reinstall ubuntu again? 

I doubt it, lets get a copy of the bootscript posted and see if any info there is relevant. 

It just may be that a purge of grub and reinstall is needed from a live cd not a big deal, grub is fairly easy to deal with in this way. It may be just a reload of grub to the mbr as well will get you in. The script will tell us if your missing anything and other important stuff.

So boot the ubuntu live cd and down load the link and extract it to your desktop and run this command and post the results.text that will appear on the desktop.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by crazycc on 2012-05-05
> **2ta8gdfte said:**
> I doubt it, lets get a copy of the bootscript posted and see if any info there is relevant. 

It just may be that a purge of grub and reinstall is needed from a live cd not a big deal, grub is fairly easy to deal with in this way. It may be just a reload of grub to the mbr as well will get you in. The script will tell us if your missing anything and other important stuff.

So boot the ubuntu live cd and down load the link and extract it to your desktop and run this command and post the results.text that will appear on the desktop.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

```
sudo bash ~/Desktop/bootinfoscript
```

Here is the information in results.text file
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos10)/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda13: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   105,064,896   104,858,049   7 NTFS / exFAT / HPFS
/dev/sda3         105,065,099 1,930,932,674 1,825,867,576   5 Extended
/dev/sda5         105,065,100   209,921,354   104,856,255   7 NTFS / exFAT / HPFS
/dev/sda6         209,921,418   272,831,894    62,910,477   7 NTFS / exFAT / HPFS
/dev/sda7         272,831,958   377,688,149   104,856,192   7 NTFS / exFAT / HPFS
/dev/sda8         377,688,213   901,969,424   524,281,212   7 NTFS / exFAT / HPFS
/dev/sda9         901,969,488 1,826,092,484   924,122,997   7 NTFS / exFAT / HPFS
/dev/sda10      1,826,092,548 1,826,526,239       433,692  83 Linux
/dev/sda11      1,826,526,303 1,893,629,744    67,103,442  83 Linux
/dev/sda12      1,893,629,808 1,914,112,619    20,482,812  83 Linux
/dev/sda13      1,914,112,683 1,930,932,674    16,819,992  82 Linux swap / Solaris
/dev/sda4       1,930,947,009 1,953,520,064    22,573,056   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 3,907,024,895 3,907,022,848   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        90A6B39BA6B37FF0                       ntfs       SYSTEM
/dev/sda10       707d28d4-bbbb-47e9-b238-30474a061ffa   ext2       
/dev/sda11       d8d39516-17b6-453c-9255-ba39adbcf7de   ext3       
/dev/sda12       0934b015-f049-4683-b1ac-29e2050bb7a7   ext3       
/dev/sda13       afc895f4-a501-4c25-bfe5-b5ef34399c79   swap       swap
/dev/sda2        A63AB52C3AB4FA7F                       ntfs       HP
/dev/sda4        6E1AB6611AB6264D                       ntfs       FACTORY_IMAGE
/dev/sda5        18E63D194E97E318                       ntfs       EP01
/dev/sda6        06B7EEB8036D407F                       ntfs       EP02
/dev/sda7        348831A4783E993B                       ntfs       Tmp
/dev/sda8        2262BB032CD12A43                       ntfs       Ent
/dev/sda9        7E73E0A3575FFF2D                       ntfs       Dl
/dev/sdb1        0CBA7BADBA7B91C6                       ntfs       Elements
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda10       /media/707d28d4-bbbb-47e9-b238-30474a061ffa ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda11       /media/d8d39516-17b6-453c-9255-ba39adbcf7de ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda12       /media/0934b015-f049-4683-b1ac-29e2050bb7a7 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda10/grub/grub.cfg: =============================

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
set default="4"
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
set root='(hd0,msdos12)'
search --no-floppy --fs-uuid --set=root 0934b015-f049-4683-b1ac-29e2050bb7a7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos10)'
  search --no-floppy --fs-uuid --set=root 707d28d4-bbbb-47e9-b238-30474a061ffa
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=20
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 707d28d4-bbbb-47e9-b238-30474a061ffa
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set=root 707d28d4-bbbb-47e9-b238-30474a061ffa
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 90A6B39BA6B37FF0
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 6E1AB6611AB6264D
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  4
               =                grub/grub.cfg                                  1
               =                initrd.img-2.6.32-41-generic                  47
               =                initrd.img-2.6.38-14-generic                  60
               =                initrd.img-3.0.0-19-generic                   87
               =                initrd.img-3.2.0-24-generic                   92
               =                vmlinuz-2.6.32-41-generic                     20
               =                vmlinuz-2.6.38-14-generic                     20
               =                vmlinuz-3.0.0-19-generic                      19
               =                vmlinuz-3.2.0-24-generic                      43

=============================== sda12/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda12 during installation
UUID=0934b015-f049-4683-b1ac-29e2050bb7a7 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda10 during installation
UUID=707d28d4-bbbb-47e9-b238-30474a061ffa /boot           ext2    defaults        0       2
# /home was on /dev/sda11 during installation
UUID=d8d39516-17b6-453c-9255-ba39adbcf7de /home           ext3    defaults        0       2
# swap was on /dev/sda13 during installation
UUID=afc895f4-a501-4c25-bfe5-b5ef34399c79 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by 2ta8gdfte on 2012-05-05
So it looks like sda12 is the install, it only shows fstab and the sda10 has most of the rest of the grub files. Take a look at this link to chroot into the ubuntu to run a purge of grub and reinstall. I would run a purge once in on that ubuntu chroot, just to clean up it is only showing fstab but that is what I would do then follow the links reload of grub after the chroot in part.

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

Command to purge any grub remnants, your in root with the chroot no sudo needed.

```
apt-get purge grub-pc grub-common
```

---

### Post by crazycc on 2012-05-05
> **2ta8gdfte said:**
> So it looks like sda12 is the install, it only shows fstab and the sda10 has most of the rest of the grub files. Take a look at this link to chroot into the ubuntu to run a purge of grub and reinstall. I would run a purge once in on that ubuntu chroot, just to clean up it is only showing fstab but that is what I would do then follow the links reload of grub after the chroot in part.

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

Command to purge any grub remnants, your in root with the chroot no sudo needed.

```
apt-get purge grub-pc grub-common
```

Thank you very much. After purging and reinstalling grub2, everything is back to normal. =D>

---

### Post by wilee-nilee on 2012-05-05
Cool, I was a little worried as I had not looked close enough at the size of that sda10 partition and did not know if that was a boot partition. This is a different user name as I had this account closed it is now open. I had only noticed it had most of the files needed with the fstab in sda12.

---

