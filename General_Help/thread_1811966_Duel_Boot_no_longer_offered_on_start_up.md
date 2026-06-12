---
title: "Duel Boot no longer offered on start up"
date: 2011-07-25
forum: General Help
---

### Post by cpcpcp on 2011-07-25
Dual boot seems to have vanished since update installed a new version of GRUB.
That is just a guess as I seldom want to run Vista but today was the day and it was not offered on restarting the machine.:(

Here is the output of Boot_Info_Script

```
                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 303713456 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   252,312,839   252,310,792   7 NTFS / exFAT / HPFS
/dev/sda2         252,313,600   262,078,463     9,764,864  82 Linux swap / Solaris
/dev/sda3         262,078,464   488,396,799   226,318,336  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   488,392,064   488,390,017   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   156,299,263   156,297,216   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   312,576,704   312,576,642   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0AC8F325C8F30DA7                       ntfs       
/dev/sda2        bafd60ed-ba6e-4939-953e-2a07bfdf43b6   swap       
/dev/sda3        ddb69d08-0136-4d38-8c72-d524a64eae6f   ext4       
/dev/sdb1        CEFCFDFBFCFDDDA1                       ntfs       
/dev/sdc1        C2E85D0AE85CFDDB                       ntfs       New Volume
/dev/sdd1        1E4C0FC74C0F9923                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sdd1        /media/1E4C0FC74C0F9923  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ddb69d08-0136-4d38-8c72-d524a64eae6f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0ac8f325c8f30da7
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=ddb69d08-0136-4d38-8c72-d524a64eae6f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=bafd60ed-ba6e-4939-953e-2a07bfdf43b6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 153.101650238 = 164.391645184  boot/grub/core.img                             1
 133.365791321 = 143.200428032  boot/grub/grub.cfg                             3
 153.121006012 = 164.412428288  boot/initrd.img-2.6.32-21-generic              1
 153.229927063 = 164.529381376  boot/initrd.img-2.6.32-23-generic              1
 153.288669586 = 164.592455680  boot/initrd.img-2.6.32-24-generic              1
 153.307052612 = 164.612194304  boot/initrd.img-2.6.32-27-generic              1
 153.264053345 = 164.566024192  boot/initrd.img-2.6.32-30-generic              1
 134.967060089 = 144.919777280  boot/initrd.img-2.6.32-31-generic              2
 128.608955383 = 138.092814336  boot/initrd.img-2.6.32-32-generic              2
 153.099941254 = 164.389810176  boot/vmlinuz-2.6.32-21-generic                 1
 153.222507477 = 164.521414656  boot/vmlinuz-2.6.32-23-generic                 1
 153.241107941 = 164.541386752  boot/vmlinuz-2.6.32-24-generic                 1
 153.233688354 = 164.533420032  boot/vmlinuz-2.6.32-27-generic                 1
 153.249214172 = 164.550090752  boot/vmlinuz-2.6.32-30-generic                 1
 153.244876862 = 164.545433600  boot/vmlinuz-2.6.32-31-generic                 1
 153.295974731 = 164.600299520  boot/vmlinuz-2.6.32-32-generic                 1
 128.608955383 = 138.092814336  initrd.img                                     2
 134.967060089 = 144.919777280  initrd.img.old                                 2
 153.295974731 = 164.600299520  vmlinuz                                        1
 153.244876862 = 164.545433600  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sde 



```

Anyone got a fix and explanation (of the fix)?

Chris

---

### Post by 3602 on 2011-07-25
Have you tried
```

sudo update-grub

```

Or it could be just the GRUB *menu* that is hidden. Hold down the Left Shift key (I don't know whether Left or Right makes a difference) right after BIOS POST to bring up the GRUB.

---

### Post by oldfred on 2011-07-25
It actually shows you have the entry.

But you also have a lot of old kernels. The grub menu box may be showing a tiny arrow on the lower right side which says you have more entries and just need to scroll down.

You may just want to houseclean out some old kernels. We normally suggest you keep two, the current & one older that you know works.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by cpcpcp on 2011-07-30
[SIZE=2]Thanks OldFred - you hit the nail on the head.
Too many entries so I had just to scroll down and keep going.

I am going to play with this the Grub Customizer later

to try to get rid of some of the entries.

Chris


It was a [SIZE=1]tiny tiny[/SIZE] arrow!
[/SIZE]

---

### Post by oldfred on 2011-07-30
I only discovered arrow after I accidentally scrolled down looking for an entry and it kept gong. then I noticed tiny arrow.

Glad you got it working.:)

---

