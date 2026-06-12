---
title: "Cannot boot linux header/kernel"
date: 2012-03-17
forum: General Help
---

### Post by Taak on 2012-03-17
Hi all.

Today I updated ubuntu using auto update, as always.

After restart I can't load the latest kernel (3.0.0.16). I'm getting this error:

"error: cannot read the Linux header. error: you need to load the kernel first."

Then I can select an older kernel version from grub2 (such as 3.0.0.15) and I can boot it without any problem.

Once in Ubuntu, I tried to reinstall kernel headers for version 3.0.0.16 from Synaptic but still I'm getting the same error. I also tried to remove - re add them.

I noticed that Synaptic didn't download the kernel again but uses the local version of the file. Is there a way to force a complete re-installation of the kernel 3.0.0.16 (downloading it again)?

Grub2 seems to be working correctly (also grub.cfg file). This is my boot info output (Ubuntu is in _**sdc**_):

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 670310352 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /GRLDR

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc3: __________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   234,438,655   234,231,808   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   669,571,071   669,569,024   7 NTFS / exFAT / HPFS
/dev/sdc2         669,571,072   693,008,383    23,437,312  83 Linux
/dev/sdc3         693,008,384   966,445,055   273,436,672  83 Linux
/dev/sdc4         966,445,056   976,771,071    10,326,016  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        92C82620C8260359                       ntfs       Archivio
/dev/sdb1        10C2455EC2454964                       ntfs       Riservato per il sistema
/dev/sdb2        E89256B19256844A                       ntfs       
/dev/sdc1        B6E6FDDFE6FDA033                       ntfs       Ubuntu e Backup
/dev/sdc2        3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4   xfs        
/dev/sdc3        ae5866bb-cc73-41b3-9b0f-f3817867f426   xfs        
/dev/sdc4        c2dc6d7b-6984-4fc4-aede-b5876e28ae08   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc2        /                        xfs        (rw)
/dev/sdc3        /home                    xfs        (rw)


=========================== sdc2/boot/grub/grub.cfg: ===========================

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
insmod xfs
set root='(hd2,msdos2)'
search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod xfs
  set root='(hd2,msdos2)'
  search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=0
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod xfs
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 92C82620C8260359
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 10C2455EC2454964
    chainloader +1
}
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

=============================== sdc2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd2 during installation
UUID=3f3237a7-f8a7-4d70-a8f6-52e7b06b3da4 /               xfs     defaults        0       1
# /home was on /dev/sdd3 during installation
UUID=ae5866bb-cc73-41b3-9b0f-f3817867f426 /home           xfs     defaults        0       2
# swap was on /dev/sdd4 during installation
UUID=c2dc6d7b-6984-4fc4-aede-b5876e28ae08 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-11-generic              1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/initrd.img-3.0.0-13-generic               1
               =                boot/initrd.img-3.0.0-14-generic               1
               =                boot/initrd.img-3.0.0-15-generic               1
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/vmlinuz-2.6.38-11-generic                 1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                boot/vmlinuz-3.0.0-15-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                 68
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                       68
               =                vmlinuz.old                                    1



```
How can I fix the kernel 3.0.0.16?

Thank you

---

### Post by Taak on 2012-03-18
Up

---

### Post by schtufbox on 2012-03-18
Can you reinstall it using Synaptic?


--ninja edit:  Doh, reading fail!  I  see you already tried that!

---

### Post by plucky on 2012-03-18
> I noticed that Synaptic didn't download the kernel again but uses the local version of the file. Is there a way to force a complete re-installation of the kernel 3.0.0.16 (downloading it again)?


```
sudo apt-get clean
``` will remove all the downloaded .deb files in /var/cache/apt/archives and synaptic will have to download another file if it has to re-install it.

If you don't want to delete all the files,then you will have to go to the archives location and delete the specific kernel .deb file.

---

