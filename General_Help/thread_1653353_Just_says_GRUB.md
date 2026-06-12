---
title: "Just says GRUB"
date: 2010-12-26
forum: General Help
---

### Post by typedino on 2010-12-26
I just installed Ubuntu 9.04. When I turn my computer on, unless I have the CD with Ubuntu on it in my drive, it goes to a screen that just says "GRUB_". I can't type or do anything, and I have to restart with the CD in. The only way I can get anywhere is if I select "Try Ubuntu without making any changes to your computer" from the installation menu. How can I fix this?

---

### Post by WorMzy on 2010-12-26
Can you boot to the liveCD (the "Try without changes" option on the CD) and download/run this script:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

It will tell us the specifics about your machine, and from that we may be able to tell you how to proceed.

---

### Post by typedino on 2010-12-26
Alright, here's what I get:
 
```
=> Grub 2 is installed in the MBR of /dev/sda and looks at sector 76962071 of 
    the same hard drive for core.img, core.img is at this location on /dev/sdc 
    and looks for (UUID=5af4dfb8-3b0e-49df-881e-3285556dd9c6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xacdd9b22

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf7ccc5b9

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    62,782,019    62,781,957   b W95 FAT32
/dev/sdc2          62,782,020   195,800,219   133,018,200   5 Extended
/dev/sdc5          62,782,083    69,400,799     6,618,717  83 Linux
/dev/sdc6         190,289,988   195,800,219     5,510,232  82 Linux swap / Solaris
/dev/sdc7          69,400,863    75,826,799     6,425,937  83 Linux
/dev/sdc8         185,261,643   190,289,924     5,028,282  82 Linux swap / Solaris
/dev/sdc9          75,826,863   180,699,119   104,872,257  83 Linux
/dev/sdc10        180,699,183   185,261,579     4,562,397  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        915D-2CFF                              vfat       My Book                       
/dev/sdc10       309c03e8-ea6e-4785-8cab-2ea61ef08159   swap                                     
/dev/sdc1        E79A-BF54                              vfat       ³²<øO&#8222;Ý¿`                   
/dev/sdc5        517403bc-9aea-4ae7-8ac5-555ab032245d   ext4                                     
/dev/sdc6        e5b365b8-29d1-48ce-b115-c3de646b2830   swap                                     
/dev/sdc7        74d57670-e406-42b6-a6e6-e348ece39376   ext4                                     
/dev/sdc8        894877dd-c181-4936-aa5a-1cac7f1734de   swap                                     
/dev/sdc9        5af4dfb8-3b0e-49df-881e-3285556dd9c6   ext4                                     
/dev/sdd1        800D-63FF                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc5        /media/517403bc-9aea-4ae7-8ac5-555ab032245d ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdd1        /media/800D-63FF         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc1        /media/E79A-BF54         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc7        /media/74d57670-e406-42b6-a6e6-e348ece39376 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdc9        /media/5af4dfb8-3b0e-49df-881e-3285556dd9c6 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1        /media/My Book           vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root=(hd2,5)
search --no-floppy --fs-uuid --set 517403bc-9aea-4ae7-8ac5-555ab032245d
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
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 517403bc-9aea-4ae7-8ac5-555ab032245d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=517403bc-9aea-4ae7-8ac5-555ab032245d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 517403bc-9aea-4ae7-8ac5-555ab032245d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=517403bc-9aea-4ae7-8ac5-555ab032245d ro single 
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
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=517403bc-9aea-4ae7-8ac5-555ab032245d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=e5b365b8-29d1-48ce-b115-c3de646b2830 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


  32.6GB: boot/grub/core.img
  32.6GB: boot/grub/grub.cfg
  32.7GB: boot/initrd.img-2.6.31-14-generic
  32.6GB: boot/vmlinuz-2.6.31-14-generic
  32.7GB: initrd.img
  32.6GB: vmlinuz

=========================== sdc7/boot/grub/grub.cfg: ===========================

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
set root=(hd1,7)
search --no-floppy --fs-uuid --set 74d57670-e406-42b6-a6e6-e348ece39376
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
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 74d57670-e406-42b6-a6e6-e348ece39376
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=74d57670-e406-42b6-a6e6-e348ece39376 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 74d57670-e406-42b6-a6e6-e348ece39376
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=74d57670-e406-42b6-a6e6-e348ece39376 ro single 
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
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 517403bc-9aea-4ae7-8ac5-555ab032245d
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=517403bc-9aea-4ae7-8ac5-555ab032245d ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 517403bc-9aea-4ae7-8ac5-555ab032245d
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=517403bc-9aea-4ae7-8ac5-555ab032245d ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=74d57670-e406-42b6-a6e6-e348ece39376 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=894877dd-c181-4936-aa5a-1cac7f1734de none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc7: Location of files loaded by Grub: ===================


  36.0GB: boot/grub/core.img
  36.0GB: boot/grub/grub.cfg
  36.0GB: boot/initrd.img-2.6.31-14-generic
  36.0GB: boot/vmlinuz-2.6.31-14-generic
  36.0GB: initrd.img
  36.0GB: vmlinuz

=========================== sdc9/boot/grub/grub.cfg: ===========================

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
set root=(hd2,9)
search --no-floppy --fs-uuid --set 5af4dfb8-3b0e-49df-881e-3285556dd9c6
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
    set root=(hd2,9)
    search --no-floppy --fs-uuid --set 5af4dfb8-3b0e-49df-881e-3285556dd9c6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5af4dfb8-3b0e-49df-881e-3285556dd9c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,9)
    search --no-floppy --fs-uuid --set 5af4dfb8-3b0e-49df-881e-3285556dd9c6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5af4dfb8-3b0e-49df-881e-3285556dd9c6 ro single 
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
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdc5)" {
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 517403bc-9aea-4ae7-8ac5-555ab032245d
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=517403bc-9aea-4ae7-8ac5-555ab032245d ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdc5)" {
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 517403bc-9aea-4ae7-8ac5-555ab032245d
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=517403bc-9aea-4ae7-8ac5-555ab032245d ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdc7)" {
    insmod ext2
    set root=(hd2,7)
    search --no-floppy --fs-uuid --set 74d57670-e406-42b6-a6e6-e348ece39376
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=74d57670-e406-42b6-a6e6-e348ece39376 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdc7)" {
    insmod ext2
    set root=(hd2,7)
    search --no-floppy --fs-uuid --set 74d57670-e406-42b6-a6e6-e348ece39376
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=74d57670-e406-42b6-a6e6-e348ece39376 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc9 during installation
UUID=5af4dfb8-3b0e-49df-881e-3285556dd9c6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc10 during installation
UUID=309c03e8-ea6e-4785-8cab-2ea61ef08159 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc9: Location of files loaded by Grub: ===================


  39.4GB: boot/grub/core.img
  39.4GB: boot/grub/grub.cfg
  39.4GB: boot/initrd.img-2.6.31-14-generic
  39.4GB: boot/vmlinuz-2.6.31-14-generic
  39.4GB: initrd.img
  39.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc
```

---

### Post by WorMzy on 2010-12-26
Hmm, this is a confusing output. According to the script, you have installed grub to your first hard disk (sda), but your first hard disk is reported as being blank. Instead, grub's files are apparently on sdc (your third hard disk)on partition 9.

Can I take this as accurate? You have one blank disk, one with a single fat32 partition, and one with multiple filesystems (primarily Linux with three swap partitions and a couple of FATs)?

If this is the case, then you probably should reinstall grub to sdc using the following tutorial/help page: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Where it says ```
sudo grub-install --root-directory=/mnt/ /dev/sdX
```
replace "X" with "c":
```
sudo grub-install --root-directory=/mnt/ /dev/sd**_c_**
```

You will probably need to modify your boot order in your bios too, unfortunately I cannot give you specific instructions on how to do this, however, I expect that you will need to press "F1" or something similar to access your bios settings during your PC's boot-up phase. The boot-up phase happens immediately after the initial splash-screen/text when you first turn on the PC.

---

### Post by typedino on 2010-12-26
Yeah, you can take all that to be true. I'm obviously no expert, and this is the first time I've ever dealt with boot problems, so I definitely appreciate your help. I'll give what you suggested a shot and see if it works.

---

### Post by Quackers on 2010-12-26
Have you tried to install Ubuntu 9.10 three times, by any chance? :-)
I ask because you appear to have 3 installations of 9.10 ( in sda5, sda7 and sda9) and you also have 3 swap partitions too).
This can be changed once you get things running ok though.

---

### Post by typedino on 2010-12-26
Ok, I got it working. I just had to figure out which of my hard drives to use. Thanks again for your help.

And yes, I did install it three times. I installed the bootloader in different places each time thinking that would work. It obviously didn't. How exactly can I change all that now? 

Also, I have a new problem, though I can probably fix this one myself:
My monitor is 1600 x 900. There is a 1600x900 option in Display Preferences, but it doesn't work properly. When I change it to another 16:9 ratio like 1360x768, it looks better, but cuts about an inch off of the top and bottom. What's going on there? Like I said, I could probably work this out myself, but if you know any solutions off the top of your head I would appreciate the help.

---

### Post by Quackers on 2010-12-26
Have you run System > Admin > Hardware Drivers to see if any video drivers are available for your graphics card?
The extra installations can be deleted, along with the swap partitions later.

---

### Post by typedino on 2010-12-26
That was the first thing I did after that last post, and it fixed it. 

So, how would I go about fixing my triple-installation mess?

---

### Post by Quackers on 2010-12-26
If you go to System > Admin > Synaptic package manager and when the screen opens type into the search box gparted and the program will appear in the main window. Right-click the gparted entry and select mark for installation, then click the green tick in the tool bar to apply the change. This will install gparted to your system.
When it's finished close synaptic and go to System > Admin > gparted and open it.
When it has scanned your hard drives it will show all your partitions. Please post a screenshot of that window in your next post.
To take a screenshot go to Applications > Accessories > Take screenshot and choose the option you want then take the screenshot. I would recommend saving it to Pictures folder.
In the forum click on New Reply (not quick reply) and then click on Manage attachments then in the window that opens click on Browse then find your Pictures folder and click on and Open the screenshot. Then click on Upload and let it run for a few seconds. When it's uploaded you can close that window and in the forum click on Submit Message, after adding any text you want.

---

### Post by typedino on 2010-12-26
Alright, here's what I'm looking at.

---

### Post by Quackers on 2010-12-26
First thing to do is right-click on all 3 swap partitions and select swapoff for all 3.
Then right-click on sdc6 and select delete. Then click on the green tick to apply that change.
Then do the same for sdc8 - deleting that partition.
Then right-click on sdc5 and select "unmount" and when it is unmounted right-click the same partition and select "delete" - then click the green tick to apply the change.
Then do the same for sdc7 - deleting that one.

After these changes right-click on sdc10 swap partition and select "swapon"
then click on the green tick mark if it's lit.

At this point you can quit gparted and open a terminal window and run
```
sudo update-grub
```
and watch the screen as grub.cfg is configured. You should see just one entry for Ubuntu (and a recovery entry) and an entry for Windows loader.

That should be it :-)  Reboot and see how things go :-)

---

### Post by typedino on 2010-12-27
Alright, I got it all straightened out. Thanks for all your help!

---

