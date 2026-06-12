---
title: "Grub2/Win XP"
date: 2010-05-12
forum: General Help
---

### Post by peridot on 2010-05-12
I could use some help if anyone could? There are many different posts on this subject, and I've tried a few things already (hope I didn't mess it up). I recently reinstalled 10.04 after the upgrade to 10.04 messed up my video settings, so this is a fresh 10.04 install with grub2. After doing so, I can't boot into XP. The os-prober detects a defunct vista and the manufacturer's rescue partition, but not XP, so I removed the execute on 30_os-prober and added one for XP (with execute) based on some posts out there and ran sudo update-grub2.

```
#! /bin/sh -e
echo "Adding Windows XP" >&2
cat << EOF
menuentry "Windows XP" {
        insmod ntfs
        set root='(hd0,5)'
        search --no-floppy --fs-uuid --set A4E0F575E0F54DD4
    drivemap -s (hd0) ${root}
        chainloader +1
}
EOF

```I also tried some variants, but they all wind up giving me a black screen with a blinking cursor instead of booting.

I also tried using an XP resuce disc and doing fixboot e: but I saw no difference. Here is the output of the script from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Note, /dev/sda5 is the partition I have XP on.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568    70,123,724    49,150,157   7 HPFS/NTFS
/dev/sda3          70,123,786   312,576,704   242,452,919   f W95 Ext d (LBA)
/dev/sda5          70,123,788   213,487,784   143,363,997   7 HPFS/NTFS
/dev/sda6         213,487,848   236,926,619    23,438,772  83 Linux
/dev/sda7         236,926,683   291,611,879    54,685,197  83 Linux
/dev/sda8         291,611,943   304,769,114    13,157,172  83 Linux
/dev/sda9         304,769,178   312,576,704     7,807,527  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,522,143 1,953,522,081   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8A108582108575CB                       ntfs       PQSERVICE                     
/dev/sda2        CAB4D6FDB4D6EB49                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda5        A4E0F575E0F54DD4                       ntfs                                     
/dev/sda6        e303b2dd-e569-4da1-9c43-dc78ca2c1e11   xfs                                      
/dev/sda7        407a21a6-f768-46e5-8027-c6cb5526684f   xfs                                      
/dev/sda8        17a78893-a9fb-47bd-9643-ef53ffb25f76   xfs                    
/dev/sda9        7a63afd2-5885-488e-b5c0-3ebd8779ab72   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4A60AAED60AADEC7                       ntfs       extra_TB                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        xfs        (rw)
/dev/sda7        /home                    xfs        (rw)
/dev/sda8        /var                     xfs        (rw)
/dev/sdb1        /TB_drive                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

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
insmod xfs
set root='(hd0,6)'
search --no-floppy --fs-uuid --set e303b2dd-e569-4da1-9c43-dc78ca2c1e11
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
insmod xfs
set root='(hd0,6)'
search --no-floppy --fs-uuid --set e303b2dd-e569-4da1-9c43-dc78ca2c1e11
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
        insmod xfs
        set root='(hd0,6)'
        search --no-floppy --fs-uuid --set e303b2dd-e569-4da1-9c43-dc78ca2c1e11
        linux   /boot/vmlinuz-2.6.32-22-generic root=UUID=e303b2dd-e569-4da1-9c43-dc78ca2c1e11 ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod xfs
        set root='(hd0,6)'
        search --no-floppy --fs-uuid --set e303b2dd-e569-4da1-9c43-dc78ca2c1e11
        echo    'Loading Linux 2.6.32-22-generic ...'
        linux   /boot/vmlinuz-2.6.32-22-generic root=UUID=e303b2dd-e569-4da1-9c43-dc78ca2c1e11 ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod xfs
        set root='(hd0,6)'
        search --no-floppy --fs-uuid --set e303b2dd-e569-4da1-9c43-dc78ca2c1e11
        linux   /boot/vmlinuz-2.6.32-21-generic root=UUID=e303b2dd-e569-4da1-9c43-dc78ca2c1e11 ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod xfs
        set root='(hd0,6)'
        search --no-floppy --fs-uuid --set e303b2dd-e569-4da1-9c43-dc78ca2c1e11
        echo    'Loading Linux 2.6.32-21-generic ...'
        linux   /boot/vmlinuz-2.6.32-21-generic root=UUID=e303b2dd-e569-4da1-9c43-dc78ca2c1e11 ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod xfs
        set root='(hd0,6)'
        search --no-floppy --fs-uuid --set e303b2dd-e569-4da1-9c43-dc78ca2c1e11
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod xfs
        set root='(hd0,6)'
        search --no-floppy --fs-uuid --set e303b2dd-e569-4da1-9c43-dc78ca2c1e11
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_Windows ###
menuentry "Windows XP" {
        insmod ntfs
        set root='(hd0,5)'
        search --no-floppy --fs-uuid --set A4E0F575E0F54DD4
        drivemap -s (hd0) 
        chainloader +1
}
### END /etc/grub.d/25_Windows ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               xfs     defaults        0       1
# /TB_drive was on /dev/sdb1 during installation
UUID=4A60AAED60AADEC7 /TB_drive       ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/sda7       /home           xfs     defaults        0       2
/dev/sda8       /var            xfs     defaults        0       2
# /windows was on /dev/sda5 during installation
UUID=A4E0F575E0F54DD4 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda9 during installation
UUID=7a63afd2-5885-488e-b5c0-3ebd8779ab72 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 116.1GB: boot/grub/core.img
 115.5GB: boot/grub/grub.cfg
 112.9GB: boot/initrd.img-2.6.32-21-generic
 112.8GB: boot/initrd.img-2.6.32-22-generic
 112.8GB: boot/vmlinuz-2.6.32-21-generic
 112.6GB: boot/vmlinuz-2.6.32-22-generic
 112.8GB: initrd.img
 112.9GB: initrd.img.old
 112.6GB: vmlinuz
 112.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 


```

---

### Post by peridot on 2010-05-13
Anyone?

Appreciate any help!

---

### Post by amyznikov on 2010-05-13
Hi,  I got the same problem on x86_64 machine, spent several hours trying to fix it, but had no success. Can someone advise something useful?  Thanks!

---

### Post by Mark Phelps on 2010-05-14
Have you tried fixboot and fixmbr with volumes other than "E:"?

---

### Post by peridot on 2010-05-14
Hi,

Thanks for the response. I managed to figure out that my windows was just kind of messed up in how it looked at things. It's working correctly now.

amyznikov, I suggest starting a thread with the output of the script from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) as it seems that the grub2/windows problems are all a tiny bit different. I've dealt with another grub2/xp problem a friend was having which was having trouble with a geom error and not a blank screen. That one I dealt with by using testdisk on the xp partition to recover the mbr.

Good luck!

---

