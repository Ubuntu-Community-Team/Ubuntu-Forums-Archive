---
title: "Can not boot Windows XP after Upgrade"
date: 2010-05-10
forum: General Help
---

### Post by sajumuhamma on 2010-05-10
Recently I upgraded Ubuntu 9.10 to Ubuntu 10.04. But now I can not boot Windows XP through grub menu. Grub menu is showing "Microsoft Windows XP Professional (on /dev/sda1)". When selecting this item nothing happening. 

Boot info of my system is 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 100381846 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 100381142 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 100381206 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda6 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 100382422 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda7 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,482,874    20,482,812   7 HPFS/NTFS
/dev/sda2          20,482,875   156,296,384   135,813,510   f W95 Ext d (LBA)
/dev/sda5          20,482,938    57,319,981    36,837,044   b W95 FAT32
/dev/sda6          57,320,045    71,682,029    14,361,985   7 HPFS/NTFS
/dev/sda7          71,682,093   100,101,014    28,418,922   b W95 FAT32
/dev/sda8         100,101,078   153,886,634    53,785,557  83 Linux
/dev/sda9         153,886,698   156,296,384     2,409,687  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        92C09FB1C09F99D5                       ntfs       Preetha                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0C57-2894                              vfat       PRAVEENA                      
/dev/sda6        A060CB0760CAE2E0                       ntfs       New Volume                    
/dev/sda7        F46B-9784                              vfat       PRATHEEKSHA                   
/dev/sda8        5a79b4f6-4a62-4996-9677-f7175229e7e3   ext4                                     
/dev/sda9        551793c3-f50f-4caf-a80a-dbb1e1dafd4d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 

================================ sda6/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
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
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 92c09fb1c09f99d5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=551793c3-f50f-4caf-a80a-dbb1e1dafd4d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  51.3GB: boot/grub/core.img
  54.5GB: boot/grub/grub.cfg
  62.0GB: boot/initrd.img-2.6.31-21-generic
  56.9GB: boot/initrd.img-2.6.32-21-generic
  61.4GB: boot/initrd.img-2.6.32-22-generic
  57.5GB: boot/vmlinuz-2.6.31-21-generic
  57.4GB: boot/vmlinuz-2.6.32-21-generic
  52.6GB: boot/vmlinuz-2.6.32-22-generic
  61.4GB: initrd.img
  56.9GB: initrd.img.old
  52.6GB: vmlinuz
  57.4GB: vmlinuz.old
```

Please help me

---

### Post by cavh on 2010-05-10
Do a search in the Ubuntu forums for *fixmbr* - the Windows command to fix the master boot record.

---

### Post by Mark Phelps on 2010-05-10
I'm seeing this problem so often now, I'm wondering if it's a generic problem with the new GRB2 installer ...

So, did you manually install GRUB to all your partitions? OR did the installer do that for you automatically?

---

### Post by ballboy on 2010-05-10
I too had this problem after upgrading to Ubuntu v10. Dual booting was working fine until the upgrade and now selecting the XP option simply reboots the PC without any further prompt.
I've done an 'upgrade-grub' and recreated the menu but it's still the same. During the upgrade process it asked me to select the boot drive and stated that if I didn't know which drive then to select all. I selected both the boot drive and to be on the safe-side also selected the linux drive (i have a number of partitions across two drives). I wonder if this has caused it to install grub on the wrong drive or have I maybe over-written the XP mbr?... I'm assuming that running a fixmbr would overwrite the grub boot record so not an ideal solution... Any suggestions how I can fix this?

---

### Post by NicoAdamo on 2010-05-10
try [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

have read some similar forums with the exact problem and it seems to be the solution, although I haven't tried it yet

---

### Post by Padapwa on 2010-05-10
> **sajumuhamma said:**
> Recently I upgraded Ubuntu 9.10 to Ubuntu 10.04. But now I can not boot Windows XP through grub menu. Grub menu is showing "Microsoft Windows XP Professional (on /dev/sda1)". When selecting this item nothing happening. 

Boot info of my system is 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 100381846 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 100381142 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 100381206 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda6 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 100382422 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda7 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,482,874    20,482,812   7 HPFS/NTFS
/dev/sda2          20,482,875   156,296,384   135,813,510   f W95 Ext d (LBA)
/dev/sda5          20,482,938    57,319,981    36,837,044   b W95 FAT32
/dev/sda6          57,320,045    71,682,029    14,361,985   7 HPFS/NTFS
/dev/sda7          71,682,093   100,101,014    28,418,922   b W95 FAT32
/dev/sda8         100,101,078   153,886,634    53,785,557  83 Linux
/dev/sda9         153,886,698   156,296,384     2,409,687  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        92C09FB1C09F99D5                       ntfs       Preetha                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0C57-2894                              vfat       PRAVEENA                      
/dev/sda6        A060CB0760CAE2E0                       ntfs       New Volume                    
/dev/sda7        F46B-9784                              vfat       PRATHEEKSHA                   
/dev/sda8        5a79b4f6-4a62-4996-9677-f7175229e7e3   ext4                                     
/dev/sda9        551793c3-f50f-4caf-a80a-dbb1e1dafd4d   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 

================================ sda6/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
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
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 5a79b4f6-4a62-4996-9677-f7175229e7e3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 92c09fb1c09f99d5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=5a79b4f6-4a62-4996-9677-f7175229e7e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=551793c3-f50f-4caf-a80a-dbb1e1dafd4d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  51.3GB: boot/grub/core.img
  54.5GB: boot/grub/grub.cfg
  62.0GB: boot/initrd.img-2.6.31-21-generic
  56.9GB: boot/initrd.img-2.6.32-21-generic
  61.4GB: boot/initrd.img-2.6.32-22-generic
  57.5GB: boot/vmlinuz-2.6.31-21-generic
  57.4GB: boot/vmlinuz-2.6.32-21-generic
  52.6GB: boot/vmlinuz-2.6.32-22-generic
  61.4GB: initrd.img
  56.9GB: initrd.img.old
  52.6GB: vmlinuz
  57.4GB: vmlinuz.old
```Please help me

Mine looks like this for windows...

# (2) Windows XP
menuentry "Windows XP" {
set root=(hd0,3)
chainloader +1
}
I am not all that familiar with Grub2 though.

To me it sounds like the installation was successful, a fixmbr/fixboot will boot you to windows right of your disk but that is all, you won't be able to boot linux then because it will effectively remove grub2 from the MBR.

If i were you i'd do a reinstall if you want to run linux, if not, a fixmbr from your xp boot cd will get you into windows.

---

### Post by oldfred on 2010-05-10
kansasnoob filed a bug report but it is not a software bug. And the software writer will probably say he is correct(technically), but for those who do not know a drive from a partition it is a problem.

Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)


This is what the instructions say  (bold by me):
If you're unsure which drive is designated as boot** drive** by your BIOS, it is often a good idea to install GRUB to all of them.        

It also says:
Note: It is possible to install GRUB to **partition** boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.

It then presents a check box with all **drives and partitions**. So everyone (And I think it its everyone) checks all the boxes.

Only **drives** sda, sdb, etc should be checked. Not **partitions** sda1, sda2, sdb1, etc. It would have been better to present just drives after the first statement or not even presented partitions as the few that would want that can run that later.

Installing to the windows partition overwrites part of the windows boot that is already in the windows boot sector or PBR.

---

### Post by sajumuhamma on 2010-05-10
> **NicoAdamo said:**
> try [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

have read some similar forums with the exact problem and it seems to be the solution, although I haven't tried it yet

:guitar:

[SIZE=4][COLOR=Magenta]Thank you very much.[/COLOR][/SIZE]
 
[SIZE=5][COLOR=Red]Now working well. [/COLOR][/SIZE]

[SIZE=6][COLOR=DarkRed]Thanks to all.[/COLOR][/SIZE]

---

### Post by ballboy on 2010-05-11
> **NicoAdamo said:**
> try [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

have read some similar forums with the exact problem and it seems to be the solution, although I haven't tried it yet

Super. This worked for me too although I didn't need to run from the CD and I selected to rebuild the MBR at the end.

Thanks!
:KS

---

