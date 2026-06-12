---
title: "Windows doesn't boot - just returns to GRUB menu"
date: 2010-07-17
forum: General Help
---

### Post by andypi on 2010-07-17
Hi,

Since upgrading to Lucid (I think), I can't boot into Windows. When I select the Windows Vista entry in GRUB, the screen goes blank for a moment before returning me to the GRUB menu.

I have tried pressing 'e' to edit the GRUB entry before booting, and what I find is that it says the root is hd0,1

Since my Windows partition is sda1 in GPartEd, should that translate to, for example hd0,0 ?

The only reason I want to boot into Windows in the first place is to install a BIOS upgrade from HP, which only works with their Windows software. If someone can suggest an alternative way of doing this then I won't need to boot into Windows at all...

Any ideas what's going on?

---

### Post by Jazzy_Jeff on 2010-07-17
What computer is this? Is there a problem with your computer that you need the BIOS update?

---

### Post by andypi on 2010-07-17
HP Compaq 6730s.

---

### Post by PiHalbe on 2010-09-14
Regardless of the BIOS issue … the main problem is GRUB not working.

I experience the same problem. Haven't booted Windows XP since Lucid and now it won't work, while it did before and nothing was changed on that partition since.

After selecting Windows from the list, I get a short blank screen (just cursor blinking) and then it returns to GRUB. BUT! The initial menu list and the returned-to menu list are not the same.

Inspecting grub.cfg, I have the same problem as andypi: GRUB detects Win XP on hd(0,1) while really it should be on hd(0,0), where ```
fdsik -l
``` finds the FAT32 partition.

I then tried to add a new entry, copying the detected Win XP and substituting hd(0,0) in the custom field. Selecting this entry produces the exact same result. Since both can't be the correct entries, I conclude that both are wrong.

I also get a short (text length and display time wise) error just before entering the GRUB menu saying something like ```
error [blah] file [blah] not found
```. The menu still works fine except for Win XP.

Maybe I should also mention that I had problems booting at all after Lucid upgrade, solving these with ```
sudo update-grub
```This is my original, detected Windows setting in grub.cfg:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ce9-cb95
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```I would be glad, if anyone could help.

---

### Post by baddnady23 on 2010-09-14
Run the script posted at this link and post the output so that others can see exactly what is going on inside your computer 

[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by PiHalbe on 2010-09-14
So, by now I found out that, apparently, I have two GRUB2s installed. One on the bootable partition sda1 and another one on my linux partition sda2. This explains the alternating menu entries, I guess.

Also, here is the result of boot_info_script_055.sh:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 41701582 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot/grub/grub.cfg /boot.ini /ntldr /NTDETECT.COM 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 159750360.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002e727

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   c W95 FAT32 (LBA)
/dev/sda2          40,965,750   143,364,059   102,398,310  83 Linux
/dev/sda3         143,364,060   159,750,359    16,386,300  82 Linux swap / Solaris
/dev/sda4         159,750,360   488,392,064   328,641,705   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000765f8

Partition  Boot         Start           End          Size  Id System

/dev/sdb2                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4CE9-CB95                              vfat                                     
/dev/sda2        aa4f6b50-b9f3-4198-8d60-1f31d438d8c3   ext4                                     
/dev/sda3        b2c7cd0b-7b5a-4084-8fe5-765dc2c11b09   swap                                     
/dev/sda4        14FD-CBD5                              vfat       data                          
/dev/sdb2        15760B8614C43653                       ntfs       n-storage                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
set locale_dir=($root)/boot/grub/locale
set lang=de
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
menuentry 'Ubuntu, mit Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-21-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    echo    'Linux 2.6.32-21-generic wird geladen …'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro single 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, mit Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, mit Linux 2.6.31-20-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    echo    'Linux 2.6.31-20-generic wird geladen …'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro single 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ce9-cb95
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


menuentry "Microsoft Windows XP Professional +" {
        insmod fat
        set root='(hd0,0)'
    search --no-floppy --fs-uuid --set 4ce9-cb95
        chainloader +1
}

menuentry "Microsoft Windows XP Professional ++-" {
    insmod chain
        insmod fat
    insmod drivemap
        set root='(hd0,0)'
    search --no-floppy --fs-uuid --set 4ce9-cb95
        chainloader +1
}

menuentry "Microsoft Windows XP Professional ++" {
    insmod chain
        insmod fat
    insmod drivemap
        set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ce9-cb95
        chainloader +1
}


menuentry "Microsoft Windows XP Professional +++" {
    insmod chain
        insmod fat
    insmod drivemap
        set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ce9-cb95
    drivemap -s (hd0) ${root}
        chainloader +1
}

### END /etc/grub.d/40_custom ###

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
set locale_dir=($root)/boot/grub/locale
set lang=de
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
menuentry 'Ubuntu, mit Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-24-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    echo    'Linux 2.6.32-24-generic wird geladen …'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro single 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-23-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    echo    'Linux 2.6.32-23-generic wird geladen …'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro single 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-22-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    echo    'Linux 2.6.32-22-generic wird geladen …'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro single 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-21-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    echo    'Linux 2.6.32-21-generic wird geladen …'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 ro single 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aa4f6b50-b9f3-4198-8d60-1f31d438d8c3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ce9-cb95
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows XP Professional +" {
    insmod chain
        insmod fat
    insmod drivemap
        set root='(hd0,0)'
    search --no-floppy --fs-uuid --set 4ce9-cb95
        chainloader +1
}

menuentry "Microsoft Windows XP Professional ++" {
    insmod chain
        insmod fat
    insmod drivemap
        set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ce9-cb95
        chainloader +1
}


menuentry "Microsoft Windows XP Professional +++" {
    insmod chain
        insmod fat
    insmod drivemap
        set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ce9-cb95
    drivemap -s (hd0) ${root}
        chainloader +1
}

### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                           /proc                 proc         defaults                                                             0  0  
# / was on /dev/sda2 during installation
# UUID=aa4f6b50-b9f3-4198-8d60-1f31d438d8c3 /               ext4    errors=remount-ro 0       1
/dev/sda2                      /                     ext4         errors=remount-ro                                                    0  1  
# swap was on /dev/sda3 during installation
# UUID=b2c7cd0b-7b5a-4084-8fe5-765dc2c11b09 none            swap    sw              0       0
/dev/sda3                      none                  swap         sw                                                                   0  0  
/dev/scd0                      /media/cdrom0         udf,iso9660  user,noauto,exec,utf8                                                0  0  
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb2                      /media/storage        ntfs         uid=MyUserName,gid=users                                                  0  1  
/dev/sda4                      /media/data           vfat         uid=MyUserName,gid=users                                                  0  1  



#
# NFS
#
====== some network shares ======

#
# SAMBA / DOAS
#
====== some more network shares ======


=================== sda2: Location of files loaded by Grub: ===================


  21.3GB: boot/grub/core.img
  38.7GB: boot/grub/grub.cfg
  52.0GB: boot/initrd.img-2.6.32-21-generic
  52.1GB: boot/initrd.img-2.6.32-22-generic
  53.3GB: boot/initrd.img-2.6.32-23-generic
  54.4GB: boot/initrd.img-2.6.32-24-generic
  64.3GB: boot/vmlinuz-2.6.32-21-generic
  58.9GB: boot/vmlinuz-2.6.32-22-generic
  51.1GB: boot/vmlinuz-2.6.32-23-generic
  52.8GB: boot/vmlinuz-2.6.32-24-generic
  54.4GB: initrd.img
  53.3GB: initrd.img.old
  52.8GB: vmlinuz
  51.1GB: vmlinuz.old
```The Information at the beginning of the file puzzles me. There should be no GRUB on sdb.

As sda GRUB2 uses the files on sda1:/boot/grub … is the other installation on sda2:/boot/grub obsolete? If so, what can I do to clean up this mess?

Thanks for your help. Very much appreciated!

---

### Post by PiHalbe on 2010-09-21
Does anyone have any suggestions?

---

### Post by wilee-nilee on 2010-09-21
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 41701582 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   **/boot/grub/grub.cfg** /boot.ini /ntldr /NTDETECT.COM 
                      ** /boot/grub/core.img**

To begin with this is a problem follow this links directions to clean out the grub from XP.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I will take a little closer look at the script, but this will stop XP from booting.

The grub-legacy in the mbr of sdb is not a issue or shouldn't be. I don't see any reference to grub-legacy other then in the mbr of sdb. I see the custom entries to the grub for XP so if this works cleaning it up just run the script yourself and look, at it, if the grub is gone from sda1 then run.
code:sudo update-grub in Ubuntu.

---

### Post by PiHalbe on 2010-09-21
Now I am confused. sda1 is my boot partition, right now. So should I set the boot-flag in palimpsest to sda2 (linux partition) then and remove it from sda1? Will this start the sda2-grub upon boot?

Thanks for your help any ways!

PS: I am not sure if this should really go into another thread or is still in line of the OP.

---

### Post by wilee-nilee on 2010-09-21
> **PiHalbe said:**
> Now I am confused. sda1 is my boot partition, right now. So should I set the boot-flag in palimpsest to sda2 (linux partition) then and remove it from sda1? Will this start the sda2-grub upon boot?

Thanks for your help any ways!

PS: I am not sure if this should really go into another thread or is still in line of the OP.

It would be best to have your own thread, but since you posted the script I responded. 

No your not changing the boot flag. Click on that link and read it carefully, you have grub files which I highlighted in the XP partition these have to be removed. This can be done most of the time by using testdisk so the link will instruct you. 

That section with the highlighted text is from the script you posted.

The only things which should be there are these.
/boot.ini /ntldr /NTDETECT.COM

---

### Post by PiHalbe on 2010-09-21
Great! I followed the advice step-by-step and it miraculously worked.

Thanks for the help! :popcorn:

And andypi, you should see if this was also your problem (because it sounded very much alike mine)!

---

### Post by wilee-nilee on 2010-09-21
> **PiHalbe said:**
> Great! I followed the advice step-by-step and it miraculously worked.

Thanks for the help! :popcorn:

And andypi, you should see if this was also your problem (because it sounded very much alike mine)!

Excellent, in my Mr Burns voice.;)

---

