---
title: "HELP!!! Cant boot into vista after 10.04 grub install"
date: 2010-07-19
forum: General Help
---

### Post by indrewjones0870 on 2010-07-19
HELP PLEASE!!! I recently upgraded to Ubuntu 10.04 from a 9.10/vista dual boot with vista being the primary OS. I can no longer boot into vista because i wasn't sure where to install grub during the upgrade and get just a blinking cursor when i try. I have tried several things but am willing to do them again. I would rather not loose all my settings and what not on vista. I'm not sure what info you need but here is a boot info script. Any help would be greatly appreciated i really need vista to work. Also, Ubuntu only seems to work in failsafe mode, not sure if that matters. THANKS!

```
     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 405983253 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

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

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

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

/dev/sda1                  63    23,246,054    23,245,992   7 HPFS/NTFS
/dev/sda2    *     23,246,055   327,950,909   304,704,855   7 HPFS/NTFS
/dev/sda3         327,950,910   488,392,064   160,441,155   5 Extended
/dev/sda5         359,309,853   483,042,419   123,732,567  83 Linux
/dev/sda6         483,042,483   488,392,064     5,349,582  82 Linux swap / Solaris
/dev/sda7         327,951,036   357,896,069    29,945,034  83 Linux
/dev/sda8         357,896,133   359,309,789     1,413,657  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3A043E77043E366B                       ntfs       RECOVERY                      
/dev/sda2        FCF81A6AF81A2384                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        65337ef6-5a0c-424a-b753-27bb0ea3a1e2   ext4                                     
/dev/sda6        418c9ef8-298f-4df9-b35c-0c85a8bab911   swap                                     
/dev/sda7        b773b520-03e6-4221-a129-1be281ad67b5   ext4                                     
/dev/sda8        83c09a0f-3e55-451c-9e84-e1d472c1c155   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /media/b773b520-03e6-4221-a129-1be281ad67b5 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/FCF81A6AF81A2384_ fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
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
search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
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
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3a043e77043e366b
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set fcf81a6af81a2384
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set b773b520-03e6-4221-a129-1be281ad67b5
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b773b520-03e6-4221-a129-1be281ad67b5 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set b773b520-03e6-4221-a129-1be281ad67b5
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b773b520-03e6-4221-a129-1be281ad67b5 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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
UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=418c9ef8-298f-4df9-b35c-0c85a8bab911 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 206.2GB: boot/grub/core.img
 206.5GB: boot/grub/grub.cfg
 184.9GB: boot/initrd.img-2.6.31-14-generic
 185.0GB: boot/initrd.img-2.6.32-22-generic
 184.5GB: boot/vmlinuz-2.6.31-14-generic
 184.7GB: boot/vmlinuz-2.6.32-22-generic
 185.0GB: initrd.img
 184.9GB: initrd.img.old
 184.7GB: vmlinuz
 184.5GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set b773b520-03e6-4221-a129-1be281ad67b5
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set b773b520-03e6-4221-a129-1be281ad67b5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b773b520-03e6-4221-a129-1be281ad67b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set b773b520-03e6-4221-a129-1be281ad67b5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b773b520-03e6-4221-a129-1be281ad67b5 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3a043e77043e366b
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fcf81a6af81a2384
    chainloader +1
}
menuentry "'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 65337ef6-5a0c-424a-b753-27bb0ea3a1e2
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=65337ef6-5a0c-424a-b753-27bb0ea3a1e2 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=b773b520-03e6-4221-a129-1be281ad67b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=83c09a0f-3e55-451c-9e84-e1d472c1c155 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 169.9GB: boot/grub/core.img
 170.4GB: boot/grub/grub.cfg
 170.3GB: boot/initrd.img-2.6.31-14-generic
 170.3GB: boot/vmlinuz-2.6.31-14-generic
 170.3GB: initrd.img
 170.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by oldfred on 2010-07-20
You needed to install grub2 to the MBR of drive sda, not partition sda1. That install may prevent your recovery from working, but I do not like recovery anyway so I am not sure you have lost anything. Recover just erases your drive and makes it "like new" or all your data is gone.

You can use your install CD as a liveCD to install grub2. If you did not download an install CD you will need one.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda


You should also get a windows repair CD just incase.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

