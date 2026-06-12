---
title: "Grub doesn't see all partitions on SATA drive in AHCI mode"
date: 2011-08-13
forum: General Help
---

### Post by w6fm on 2011-08-13
I have a Dell Latitude E5410 set up to multi boot Windows 7, Ubuntu 10.04 and Ubuntu 11.04. It has a 500 gb SATA drive. The SATA controller was set in the bios to AHCI mode when I installed 11.04. I could not boot into 11.04 after the install. At the grub command prompt, ls revealed that grub was only seeing partitions 1,2,5 and 6 and not 9 or 10 where 11.04 was installed. When I set the SATA controller in the bios to the ATA mode, grub now sees all partitions on the drive and 11.04 boots. Of course Windows 7 will not boot in the ATA mode.

I have attached a copy of the results from the boot info script. Why can't grub see all partitions when the disk controller is in AHCI mode?

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/grub.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   204,799,999   204,593,152   7 NTFS / exFAT / HPFS
/dev/sda3         204,802,046   331,700,223   126,898,178   5 Extended
/dev/sda5         204,802,048   224,331,775    19,529,728  83 Linux
/dev/sda6         224,333,824   243,866,699    19,532,876  83 Linux
/dev/sda7         290,740,224   331,700,223    40,960,000  83 Linux
/dev/sda8         271,209,393   278,824,139     7,614,747  82 Linux swap / Solaris
/dev/sda9         243,867,648   244,367,359       499,712  83 Linux
/dev/sda10        278,824,960   290,725,887    11,900,928  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F0C01F5FC01F2AFC                       ntfs       System Reserved
/dev/sda10       bedf8559-6444-4e69-a080-0f9389cc6163   ext4       
/dev/sda2        7E063B76063B2F11                       ntfs       
/dev/sda5        c96c6b5e-0105-4ca3-aab2-037bad2ff25c   ext4       
/dev/sda6        5fb61d5d-fd5d-4719-a88b-490d98352d6f   ext4       
/dev/sda7        e4b401d9-517c-43e2-bf27-111087904d75   ext4       
/dev/sda8        670182f8-714f-4e7d-b316-ffdc4f21b043   swap       
/dev/sda9        62c308d2-cb7a-4171-a865-39c4fd877648   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
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
search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sda5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux    /boot/vmlinuz-2.6.38-7-generic root=/dev/sda5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    echo    'Loading Linux 2.6.38-7-generic ...'
    linux    /boot/vmlinuz-2.6.38-7-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux    /boot/vmlinuz-2.6.38-5-generic root=/dev/sda5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    echo    'Loading Linux 2.6.38-5-generic ...'
    linux    /boot/vmlinuz-2.6.38-5-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-5-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux    /boot/vmlinuz-2.6.32-32-generic root=/dev/sda5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux    /boot/vmlinuz-2.6.32-30-generic root=/dev/sda5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux    /boot/vmlinuz-2.6.32-29-generic root=/dev/sda5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux    /boot/vmlinuz-2.6.32-28-generic root=/dev/sda5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set F0C01F5FC01F2AFC
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda10)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 62c308d2-cb7a-4171-a865-39c4fd877648
    linux /vmlinuz-2.6.38-8-generic root=UUID=bedf8559-6444-4e69-a080-0f9389cc6163 ro quiet splash vt.handoff=7
    initrd /initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda10)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 62c308d2-cb7a-4171-a865-39c4fd877648
    linux /vmlinuz-2.6.38-8-generic root=UUID=bedf8559-6444-4e69-a080-0f9389cc6163 ro single
    initrd /initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c96c6b5e-0105-4ca3-aab2-037bad2ff25c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=e4b401d9-517c-43e2-bf27-111087904d75 /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=670182f8-714f-4e7d-b316-ffdc4f21b043 none            swap    sw              0       0
192.168.44.1:/home/samba /home/samba nfs rsize=8192,wsize=8192,timeo=14,intr
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 103.850746155 = 111.508889600  boot/grub/core.img                             1
 104.555675507 = 112.265801728  boot/grub/grub.cfg                             1
 104.539653778 = 112.248598528  boot/initrd.img-2.6.32-28-generic              1
 104.582405090 = 112.294502400  boot/initrd.img-2.6.32-29-generic              1
 105.008403778 = 112.751915008  boot/initrd.img-2.6.32-30-generic              1
 105.570838928 = 113.355825152  boot/initrd.img-2.6.32-32-generic              1
 104.678943634 = 112.398159872  boot/initrd.img-2.6.38-5-generic               2
  98.961914062 = 106.259546112  boot/initrd.img-2.6.38-7-generic               2
  99.133789062 = 106.444095488  boot/initrd.img-2.6.38-8-generic               2
 104.476764679 = 112.181071872  boot/vmlinuz-2.6.32-28-generic                 1
 104.543418884 = 112.252641280  boot/vmlinuz-2.6.32-29-generic                 1
 104.922077179 = 112.659222528  boot/vmlinuz-2.6.32-30-generic                 1
 105.547229767 = 113.330475008  boot/vmlinuz-2.6.32-32-generic                 1
 104.586627960 = 112.299036672  boot/vmlinuz-2.6.38-5-generic                  1
 104.942699432 = 112.681365504  boot/vmlinuz-2.6.38-7-generic                  1
 104.684890747 = 112.404545536  boot/vmlinuz-2.6.38-8-generic                  1
 105.570838928 = 113.355825152  initrd.img                                     1
  99.133789062 = 106.444095488  initrd.img.old                                 2
 105.547229767 = 113.330475008  vmlinuz                                        1
 104.684890747 = 112.404545536  vmlinuz.old                                    1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set F0C01F5FC01F2AFC
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda10)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 62c308d2-cb7a-4171-a865-39c4fd877648
    linux /vmlinuz-2.6.38-8-generic root=UUID=bedf8559-6444-4e69-a080-0f9389cc6163 ro quiet splash vt.handoff=7
    initrd /initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda10)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 62c308d2-cb7a-4171-a865-39c4fd877648
    linux /vmlinuz-2.6.38-8-generic root=UUID=bedf8559-6444-4e69-a080-0f9389cc6163 ro single
    initrd /initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-7-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-7-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-5-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-5-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, with Linux 2.6.32-32-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-32-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, with Linux 2.6.32-32-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-32-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-30-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-30-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-29-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-29-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=e4b401d9-517c-43e2-bf27-111087904d75 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=40cc2e5d-fe02-4c3c-a2cc-c60f499102d3 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 109.215927124 = 117.269708800  boot/grub/core.img                             1
 112.079357147 = 120.344293376  boot/grub/grub.cfg                             1
 109.353469849 = 117.417394176  boot/initrd.img-2.6.32-28-generic              1
 109.487751007 = 117.561577472  boot/initrd.img-2.6.32-30-generic              1
 109.870841980 = 117.972918272  boot/initrd.img-2.6.32-33-generic              1
 109.294792175 = 117.354389504  boot/vmlinuz-2.6.32-28-generic                 1
 109.357250214 = 117.421453312  boot/vmlinuz-2.6.32-30-generic                 1
 109.863052368 = 117.964554240  boot/vmlinuz-2.6.32-33-generic                 1
 109.870841980 = 117.972918272  initrd.img                                     1
 109.487751007 = 117.561577472  initrd.img.old                                 1
 109.863052368 = 117.964554240  vmlinuz                                        1
 109.357250214 = 117.421453312  vmlinuz.old                                    1

============================= sda9/grub/grub.cfg: ==============================

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
set root='(/dev/sda,msdos10)'
search --no-floppy --fs-uuid --set=root bedf8559-6444-4e69-a080-0f9389cc6163
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 62c308d2-cb7a-4171-a865-39c4fd877648
set locale_dir=($root)/grub/locale
set lang=en_US
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
    search --no-floppy --fs-uuid --set=root 62c308d2-cb7a-4171-a865-39c4fd877648
    linux    /vmlinuz-2.6.38-10-generic root=UUID=bedf8559-6444-4e69-a080-0f9389cc6163 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 62c308d2-cb7a-4171-a865-39c4fd877648
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /vmlinuz-2.6.38-10-generic root=UUID=bedf8559-6444-4e69-a080-0f9389cc6163 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 62c308d2-cb7a-4171-a865-39c4fd877648
    linux    /vmlinuz-2.6.38-8-generic root=UUID=bedf8559-6444-4e69-a080-0f9389cc6163 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 62c308d2-cb7a-4171-a865-39c4fd877648
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=bedf8559-6444-4e69-a080-0f9389cc6163 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
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
    search --no-floppy --fs-uuid --set=root 62c308d2-cb7a-4171-a865-39c4fd877648
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 62c308d2-cb7a-4171-a865-39c4fd877648
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root F0C01F5FC01F2AFC
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-7-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-7-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-7-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-5-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, with Linux 2.6.38-5-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.38-5-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.38-5-generic
}
menuentry "Ubuntu, with Linux 2.6.32-32-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-32-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, with Linux 2.6.32-32-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-32-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-30-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-30-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-29-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-29-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda5 ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root c96c6b5e-0105-4ca3-aab2-037bad2ff25c
    linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda5 ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro quiet splash
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro single
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 5fb61d5d-fd5d-4719-a88b-490d98352d6f
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=5fb61d5d-fd5d-4719-a88b-490d98352d6f ro single
    initrd /boot/initrd.img-2.6.32-28-generic
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

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 116.298578262 = 124.874647552  grub/core.img                                  1
 116.304212570 = 124.880697344  grub/grub.cfg                                  1
 116.346500397 = 124.926103552  initrd.img-2.6.38-10-generic                   2
 116.377467155 = 124.959353856  initrd.img-2.6.38-8-generic                    3
 116.310857773 = 124.887832576  vmlinuz-2.6.38-10-generic                      2
 116.303042412 = 124.879440896  vmlinuz-2.6.38-8-generic                       1

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=bedf8559-6444-4e69-a080-0f9389cc6163 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda9 during installation
UUID=62c308d2-cb7a-4171-a865-39c4fd877648 /boot           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=670182f8-714f-4e7d-b316-ffdc4f21b043 none            swap    sw              0       0
UUID=e4b401d9-517c-43e2-bf27-111087904d75 /home           ext4    defaults        0       2
--------------------------------------------------------------------------------

---

