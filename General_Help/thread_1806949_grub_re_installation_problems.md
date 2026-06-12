---
title: "grub re installation problems"
date: 2011-07-18
forum: General Help
---

### Post by nk1 on 2011-07-18
I was trying to reinstall grub over my new windows installation.  I was trying from the ubuntu site 

      [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Unfortunately the step where they said to enter this command 

    sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda

I did not change the last part. So while my system reserved partition is /dev/sda1 my entire partition was /dev/sda !!!

Now when i try to startup all i get is grub console with grub> written. However i observe using gparted that the partitions still exist.

Is there any way I can retrieve the stuff back or am i done ???

---

### Post by sanderd17 on 2011-07-18
Unless you have a separate /boot partition (which I highly doubt), you forgot the /boot after /media/xxxxxxxxxxxxxxxxxxxxxx. Check the tutorial again.

If that doesn't solve it, post the output of the boot info script: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

**EDIT: What version of Ubuntu are you using, for 11.04, you need to use --boot-directory, for others it is --root-directory**

---

### Post by nk1 on 2011-07-18
No I did'nt....

My main concern right now is that grub loads in a console. Here are the results of boot info script....
```

======================================================

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 9 for /boot/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   133,050,329   132,843,482   7 NTFS / exFAT / HPFS
/dev/sda3         133,050,391   625,137,344   492,086,954   f W95 Extended (LBA)
/dev/sda5         133,050,393   248,654,069   115,603,677   7 NTFS / exFAT / HPFS
/dev/sda6         248,654,133   411,680,767   163,026,635   7 NTFS / exFAT / HPFS
/dev/sda7         465,620,992   468,037,631     2,416,640  82 Linux swap / Solaris
/dev/sda8         468,037,773   625,137,344   157,099,572   7 NTFS / exFAT / HPFS
/dev/sda9         411,682,816   459,601,919    47,919,104  83 Linux
/dev/sda10        459,603,968   465,612,799     6,008,832  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CA9C543D9C5425EB                       ntfs       System Reserved
/dev/sda10       541880fe-7476-4c35-8cdd-6cad5b133cdb   swap       
/dev/sda2        0AD679F2D679DDFF                       ntfs       
/dev/sda5        E810E5E210E5B7A8                       ntfs       Setups
/dev/sda6        F466038966034BB4                       ntfs       College
/dev/sda7        cba379c5-3281-458a-8e26-05a6201f71bd   swap       
/dev/sda8        B2C01A35C01A0071                       ntfs       Media
/dev/sda9        268eff67-4436-4f73-9531-2428e4f7b8d4   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Setups            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/College           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda9/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda9       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=541880fe-7476-4c35-8cdd-6cad5b133cdb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 208.459011078 = 223.831158784  boot/grub/core.img                             1
 217.115474701 = 233.125965824  boot/grub/grub.cfg                             1
 213.441162109 = 229.180702720  boot/initrd.img-2.6.38-10-generic              2
 198.235351562 = 212.853587968  boot/initrd.img-2.6.38-8-generic               2
 213.032535553 = 228.741943296  boot/vmlinuz-2.6.38-10-generic                 1
 208.458633423 = 223.830753280  boot/vmlinuz-2.6.38-8-generic                  1
 213.441162109 = 229.180702720  initrd.img                                     2
 198.235351562 = 212.853587968  initrd.img.old                                 2
 213.032535553 = 228.741943296  vmlinuz                                        1
 208.458633423 = 223.830753280  vmlinuz.old                                    1
```

---

### Post by sanderd17 on 2011-07-18
Please read the entire boot info script page. It clearly says you have to click the # symbol to put it between code tags.

I can't read code that isn't aligned.

---

### Post by nk1 on 2011-07-18
Sorry about that....

This time i am placing the results inside the code tag.........

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 9 for /boot/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   133,050,329   132,843,482   7 NTFS / exFAT / HPFS
/dev/sda3         133,050,391   625,137,344   492,086,954   f W95 Extended (LBA)
/dev/sda5         133,050,393   248,654,069   115,603,677   7 NTFS / exFAT / HPFS
/dev/sda6         248,654,133   411,680,767   163,026,635   7 NTFS / exFAT / HPFS
/dev/sda7         465,620,992   468,037,631     2,416,640  82 Linux swap / Solaris
/dev/sda8         468,037,773   625,137,344   157,099,572   7 NTFS / exFAT / HPFS
/dev/sda9         411,682,816   459,601,919    47,919,104  83 Linux
/dev/sda10        459,603,968   465,612,799     6,008,832  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CA9C543D9C5425EB                       ntfs       System Reserved
/dev/sda10       541880fe-7476-4c35-8cdd-6cad5b133cdb   swap       
/dev/sda2        0AD679F2D679DDFF                       ntfs       
/dev/sda5        E810E5E210E5B7A8                       ntfs       Setups
/dev/sda6        F466038966034BB4                       ntfs       College
/dev/sda7        cba379c5-3281-458a-8e26-05a6201f71bd   swap       
/dev/sda8        B2C01A35C01A0071                       ntfs       Media
/dev/sda9        268eff67-4436-4f73-9531-2428e4f7b8d4   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Setups            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/College           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda9/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda9       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=541880fe-7476-4c35-8cdd-6cad5b133cdb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 208.459011078 = 223.831158784  boot/grub/core.img                             1
 217.115474701 = 233.125965824  boot/grub/grub.cfg                             1
 213.441162109 = 229.180702720  boot/initrd.img-2.6.38-10-generic              2
 198.235351562 = 212.853587968  boot/initrd.img-2.6.38-8-generic               2
 213.032535553 = 228.741943296  boot/vmlinuz-2.6.38-10-generic                 1
 208.458633423 = 223.830753280  boot/vmlinuz-2.6.38-8-generic                  1
 213.441162109 = 229.180702720  initrd.img                                     2
 198.235351562 = 212.853587968  initrd.img.old                                 2
 213.032535553 = 228.741943296  vmlinuz                                        1
 208.458633423 = 223.830753280  vmlinuz.old                                    1




```

---

### Post by Elfy on 2011-07-18
Hi - next time instead of double posting you can just edit the post :)

Duplicate deleted.

Just as a fyi - if you can't find the # button (Quick reply does not have it) putting [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end is the same.

---

### Post by sanderd17 on 2011-07-18
> **nk1 said:**
> Sorry about that....

This time i am placing the results inside the code tag.........


ok, it looks better now.

> 

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 9 for /boot/boot/grub.


```


Now you seem to have a boot to much. Is this your original command? or what command did you use?

> 
```


sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  


```

Wow, 5 Windows partitions and 2 swap partitions. Why do you have so many partitions? I don't know if you can boot with 2 swap partitions, so please delete one. 
> 

```


============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   133,050,329   132,843,482   7 NTFS / exFAT / HPFS
/dev/sda3         133,050,391   625,137,344   492,086,954   f W95 Extended (LBA)
/dev/sda5         133,050,393   248,654,069   115,603,677   7 NTFS / exFAT / HPFS
/dev/sda6         248,654,133   411,680,767   163,026,635   7 NTFS / exFAT / HPFS
/dev/sda7         465,620,992   468,037,631     2,416,640  82 Linux swap / Solaris
/dev/sda8         468,037,773   625,137,344   157,099,572   7 NTFS / exFAT / HPFS
/dev/sda9         411,682,816   459,601,919    47,919,104  83 Linux
/dev/sda10        459,603,968   465,612,799     6,008,832  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CA9C543D9C5425EB                       ntfs       System Reserved
/dev/sda10       541880fe-7476-4c35-8cdd-6cad5b133cdb   swap       
/dev/sda2        0AD679F2D679DDFF                       ntfs       
/dev/sda5        E810E5E210E5B7A8                       ntfs       Setups
/dev/sda6        F466038966034BB4                       ntfs       College
/dev/sda7        cba379c5-3281-458a-8e26-05a6201f71bd   swap       
/dev/sda8        B2C01A35C01A0071                       ntfs       Media
/dev/sda9        268eff67-4436-4f73-9531-2428e4f7b8d4   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Setups            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/College           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda9/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=268eff67-4436-4f73-9531-2428e4f7b8d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 268eff67-4436-4f73-9531-2428e4f7b8d4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda9       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=541880fe-7476-4c35-8cdd-6cad5b133cdb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 208.459011078 = 223.831158784  boot/grub/core.img                             1
 217.115474701 = 233.125965824  boot/grub/grub.cfg                             1
 213.441162109 = 229.180702720  boot/initrd.img-2.6.38-10-generic              2
 198.235351562 = 212.853587968  boot/initrd.img-2.6.38-8-generic               2
 213.032535553 = 228.741943296  boot/vmlinuz-2.6.38-10-generic                 1
 208.458633423 = 223.830753280  boot/vmlinuz-2.6.38-8-generic                  1
 213.441162109 = 229.180702720  initrd.img                                     2
 198.235351562 = 212.853587968  initrd.img.old                                 2
 213.032535553 = 228.741943296  vmlinuz                                        1
 208.458633423 = 223.830753280  vmlinuz.old                                    1




```

---

### Post by nk1 on 2011-07-18
Hey ,

Thanks for your reply...

I had 4 windows partition and the first partition is the system reserved partition on which i should have installed grub...

As regards to the swap i don't think that is the problem since i was running the system before too... However when i try to delete it using gparted from a live cd the options to delete swap get greyed out... Do you know why that could be happening?

Is there any way to get out of the previous grub installation ? If i try it again on ```
/dev/sda1
``` would it get replaced ?

---

### Post by Elfy on 2011-07-18
> I don't know if you can boot with 2 swap partitions, so please delete one. You can - though only one will be mounted with fstab - the other is just sitting there.

---

### Post by sanderd17 on 2011-07-18
> **nk1 said:**
> Hey ,

Thanks for your reply...

I had 4 windows partition and the first partition is the system reserved partition on which i should have installed grub...

it's impossible (or at least very hard) to install GRUB to a windows partition. So try to install it to another partition
> 

As regards to the swap i don't think that is the problem since i was running the system before too... However when i try to delete it using gparted from a live cd the options to delete swap get greyed out... Do you know why that could be happening?

that's generally because swap is used, you have to right click and select "unmount" first
> 

Is there any way to get out of the previous grub installation ? If i try it again on ```
/dev/sda1
``` would it get replaced ?

the /dev/sda has to be that way, sda is your harddisk, not a partition. But you should mount your ubuntu partition (/dev/sda9) to /media/xxxxxxxxxxx

[B]EDIT: just to be sure, you didn't copy the part after /media did you? That weird string is different for everyone (that's why I type xxxxxxxx). You must use your own string. 
Type
```

ls /media

```
to see what strings are available.[/B]

---

### Post by nk1 on 2011-07-18
I have tried it many times but the same thing is happening....

I mount the ubuntu partition , get its info using ```
mount | tail -1 
``` ant then use that number in grub installation command.

The terminal ends with installation finished and no error but when I restart grub boots in command line...

I don't know what is the problem... Have checked that i have grub2 and using ubuntu 10.04 live cd...

---

### Post by sanderd17 on 2011-07-18
You have 11.04 installed, so you should use the 11.04 live CD to get everything ok. Was 10.04 a typo? Or did you use the wrong disk?

May I ask you to give me the exact command like you typed it?

Was it --root-directory or --boot-directory? Did you do /media/xxxxxx/boot or just /media/xxxxxxx?

---

