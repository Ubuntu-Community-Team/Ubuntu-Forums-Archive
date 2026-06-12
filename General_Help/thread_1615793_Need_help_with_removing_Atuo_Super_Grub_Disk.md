---
title: "Need help with removing Atuo Super Grub Disk"
date: 2010-11-07
forum: General Help
---

### Post by neonfire999 on 2010-11-07
Ok, so a while ago, my computer screwed up and the MBR or GRUB was screwed up, so I got my Windows 7 repair disk and repaired the MBR. Then I needed grub back so I could boot into Ubuntu so I went and looked for something to just install grub and found this Auto Super GRUB Disk (ASGD) thing. So I installed it and then it appeared on the windows boot manager menu when I started up and I went into it and installed grub again. Then when I booted back into windows, it asked me if I wanted to remove ASGD and I clicked yes. Ever since, the ASGD entry has not been removed from my boot menu for some stupid reason. What happens is the computer starts and goes into GRUB which is what I want and then if I go into Windows 7, it will then come up with another menu asking whether to boot into Windows 7 or the ASGD, even though ASGD isn't there anymore. I can still boot into windows, but this extra menu that comes up every time is starting to **** me off. I've tried EasyBCD and the entry does not come up on there. If anyone has any idea how to remove this empty entry, that'd be great. Thanks.

---

### Post by dino99 on 2010-11-07
dont use w7 myself (im a ubunteros :)) but you could update its bootloader, or run regedit to search about ASGD and delete entries.

---

### Post by neonfire999 on 2010-11-07
> **dino99 said:**
> dont use w7 myself (im a ubunteros :)) but you could update its bootloader, or run regedit to search about ASGD and delete entries.

ok well, i have no idea how to update the bootloader, and using the windows 7 disk to repair it will just replace grub. Also, i searched the registry for grub and found nothing to do with the bootloader or anything.

---

### Post by wilee-nilee on 2010-11-07
> **neonfire999 said:**
> ok well, i have no idea how to update the bootloader, and using the windows 7 disk to repair it will just replace grub. Also, i searched the registry for grub and found nothing to do with the bootloader or anything.

Post the bootscript in my signature if you can. Post it in code tags by pasting the text from the generated file from running the script to a reply highlight all the text and then click on the # in the reply panel.

---

### Post by neonfire999 on 2010-12-19
> **wilee-nilee said:**
> Post the bootscript in my signature if you can. Post it in code tags by pasting the text from the generated file from running the script to a reply highlight all the text and then click on the # in the reply panel.

alright, sorry that took so long. I got caught up doing other things over the last few months and never got around to doing this, but here is the results from that script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2          31,459,328    31,664,127       204,800   7 HPFS/NTFS
/dev/sda3          31,664,128   871,558,379   839,894,252   7 HPFS/NTFS
/dev/sda4         871,567,358   976,773,119   105,205,762   f W95 Ext d (LBA)
/dev/sda5         871,567,360   972,380,159   100,812,800  83 Linux
/dev/sda6         972,382,208   976,773,119     4,390,912  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6A24DBB924DB870B                       ntfs       RECOVERY                      
/dev/sda2        4AC6DC3BC6DC28C9                       ntfs       SYSTEM                        
/dev/sda3        B4B2DE26B2DDED3C                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        6bb3ae05-db88-4452-9b64-5d414341e85d   ext4                                     
/dev/sda6        39d62379-a011-4361-8be8-c3c76bcf368f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/B4B2DE26B2DDED3C  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 6bb3ae05-db88-4452-9b64-5d414341e85d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 6bb3ae05-db88-4452-9b64-5d414341e85d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4ac6dc3bc6dc28c9
    chainloader +1
}
menuentry 'Ubuntu 10.04' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6bb3ae05-db88-4452-9b64-5d414341e85d
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6bb3ae05-db88-4452-9b64-5d414341e85d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry "Windows 7 Recovery" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6a24dbb924db870b
    chainloader +1
}
menuentry 'Ubuntu 10.04 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6bb3ae05-db88-4452-9b64-5d414341e85d
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6bb3ae05-db88-4452-9b64-5d414341e85d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6bb3ae05-db88-4452-9b64-5d414341e85d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6bb3ae05-db88-4452-9b64-5d414341e85d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6bb3ae05-db88-4452-9b64-5d414341e85d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=39d62379-a011-4361-8be8-c3c76bcf368f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 487.1GB: boot/grub/core.img
 461.6GB: boot/grub/grub.cfg
 489.2GB: boot/initrd.img-2.6.32-22-generic
 489.7GB: boot/initrd.img-2.6.35-22-generic
 487.3GB: boot/vmlinuz-2.6.32-22-generic
 487.3GB: boot/vmlinuz-2.6.35-22-generic
 489.7GB: initrd.img
 487.3GB: vmlinuz
```

---

### Post by neonfire999 on 2011-01-16
bump.

---

