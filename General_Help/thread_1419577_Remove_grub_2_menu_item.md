---
title: "Remove grub 2 menu item"
date: 2010-03-02
forum: General Help
---

### Post by lindsay7 on 2010-03-02
I am dual booting Windows 7 sda1 and Ubuntu 9.10 on one hard drive. The second hard drive is data only. My grub menu shows at the end of the menu  

Windows 7 sda1

Windows 7 sdb1

I think this is because I had a bad "A" drive that I just replaced and before that I did a lot of changing of the mbr and grub commands. So there must be something on the "B" or second drive that is causing this.  Right now everything is fine with my computer and this is just house keeping. I would like to delete the "Windows 7 sdb1" menu Item if possible.

Can you, please,  help me with this?

Just to be clear, windows boots with the sda1 command (first menu Item), and the "windows 7 sdb1" does nothing at all.

---

### Post by lindsay7 on 2010-03-03
Here the boot script.  I can see what the problem is on sdb1, but I do not know how to fix this.

```
        Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 617199464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdcc734c6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,854,449   586,854,387   7 HPFS/NTFS
/dev/sda2         586,856,448   731,278,799   144,422,352  83 Linux
/dev/sda3         731,278,800   976,768,064   245,489,265   5 Extended
/dev/sda5         731,294,865   743,006,249    11,711,385  82 Linux swap / Solaris
/dev/sda6         743,006,313   976,768,064   233,761,752  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99d2cca0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,769,023   976,766,976   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        442604C22604B6C8                       ntfs                                     
/dev/sda2        fd027f5c-7e2e-4161-84b4-c4b32265a175   ext4                                     
/dev/sda5        031a2a69-63d5-465f-bbe8-ca43d957b05a   swap                                     
/dev/sda6        8aaf3307-6206-4e45-b365-49b16e4bc88a   ext4                                     
/dev/sdb1        CACAEC03CAEBEA21                       ntfs       adrive                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set default="8"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
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
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
insmod tga
if background_image /boot/grub/Lake_mapourika_NZ.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 442604c22604b6c8
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set cacaec03caebea21
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=031a2a69-63d5-465f-bbe8-ca43d957b05a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 321.4GB: boot/grub/core.img
 315.8GB: boot/grub/grub.cfg
 320.0GB: boot/initrd.img-2.6.31-14-generic
 321.5GB: boot/initrd.img-2.6.31-15-generic
 321.8GB: boot/initrd.img-2.6.31-20-generic
 302.9GB: boot/vmlinuz-2.6.31-14-generic
 316.4GB: boot/vmlinuz-2.6.31-15-generic
 321.4GB: boot/vmlinuz-2.6.31-20-generic
 321.8GB: initrd.img
 321.5GB: initrd.img.old
 321.4GB: vmlinuz
 316.4GB: vmlinuz.old
```

---

### Post by meierfra. on 2010-03-03
> 
sdb1: _
    Boot files/dirs:   /bootmgr /Boot/BCD

Just deleted those files and run update-grub

```
sudo mount /dev/sdb1 /mnt
sudo rm /mnt/bootmgr
sudo rm -r /mnt/Boot
sudo update-grub
```

---

### Post by lindsay7 on 2010-03-03
Perfect!!


Thank you again. It is just great that you help so many people  and have the patients to do so.

---

