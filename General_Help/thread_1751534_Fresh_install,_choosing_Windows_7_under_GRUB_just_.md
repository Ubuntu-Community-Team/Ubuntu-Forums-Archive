---
title: "Fresh install, choosing Windows 7 under GRUB just restarts system."
date: 2011-05-06
forum: General Help
---

### Post by HHx66 on 2011-05-06
I just installed the newest version of Xubuntu using the LiveCD, I chose to install it alongside my current installation of Windows 7, everything went well it seemed, but now when I choose Windows 7 under the GRUB menu it just restarts my system and then takes me back to the grub menu, Xubuntu works fine though and boots fine, I tried sudo update-grub, didn't fix it.

Heres the boot info from a script I found, but being rather poor when it comes to diagnosing Linux, I figured it'd be best to post this and see if someone can please help:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Grub 2 is installed in the MBR of /dev/mapper/nvidia_daaeebgi and looks on 
    the same drive in partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

nvidia_daaeebgi1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *          2,048       208,844       206,797   7 HPFS/NTFS
/dev/sda2             208,845   156,312,449   156,103,605   7 HPFS/NTFS
/dev/sda3         156,312,511   312,580,095   156,267,585   f W95 Ext d (LBA)
/dev/sda5         156,312,513   234,340,014    78,027,502   7 HPFS/NTFS
/dev/sda6         309,442,560   312,580,095     3,137,536  82 Linux swap / Solaris
/dev/sda7         234,340,352   306,286,591    71,946,240  83 Linux
/dev/sda8         306,288,640   309,428,223     3,139,584  82 Linux swap / Solaris


Drive: nvidia_daaeebgi ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_daaeebgi: 250.1 GB, 250059348992 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_daaeebgi1                 63   488,279,609   488,279,547   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/nvidia_daaeebgi1 0AC6B200C6B1EC57                       ntfs                                     
/dev/mapper/nvidia_daaeebgi: PTTYPE="dos" 
/dev/sda1        85DE2A938CDB989A                       ntfs       System Reserved               
/dev/sda2        F73EF26E6517672B                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        01CBBB1B40C7FB30                       ntfs                                     
/dev/sda6        a85a8f23-dbb1-451e-9130-b7da356f8faf   swap                                     
/dev/sda7        d245d3c1-7c76-4e26-9e5c-bc0c75d1bddf   ext4                                     
/dev/sda8        d8f11477-d710-40f8-8649-58d5db4df31a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb                                                nvidia_raid_member                               
error: and: No such file or directory
error: /dev/mapper//dev/sdb:: No such file or directory
error: discovered: No such file or directory
error: formats: No such file or directory
error: "nvidia": No such file or directory
error: nvidia)!: No such file or directory
error: "pdc": No such file or directory
error: (using: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
nvidia_daaeebgi
nvidia_daaeebgi1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root d245d3c1-7c76-4e26-9e5c-bc0c75d1bddf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root d245d3c1-7c76-4e26-9e5c-bc0c75d1bddf
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root d245d3c1-7c76-4e26-9e5c-bc0c75d1bddf
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d245d3c1-7c76-4e26-9e5c-bc0c75d1bddf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root d245d3c1-7c76-4e26-9e5c-bc0c75d1bddf
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d245d3c1-7c76-4e26-9e5c-bc0c75d1bddf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root d245d3c1-7c76-4e26-9e5c-bc0c75d1bddf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root d245d3c1-7c76-4e26-9e5c-bc0c75d1bddf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 85DE2A938CDB989A
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=d8f11477-d710-40f8-8649-58d5db4df31a none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 128.8GB: boot/grub/core.img
 137.5GB: boot/grub/grub.cfg
 121.3GB: boot/initrd.img-2.6.38-8-generic
 128.7GB: boot/vmlinuz-2.6.38-8-generic
 121.3GB: initrd.img
 128.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb: "pdc" and "nvidia" formats discovered (using nvidia)! 
=============================== StdErr Messages: ===============================

ERROR: only one argument allowed for this option
ERROR: only one argument allowed for this option

```

---

### Post by slooksterpsv on 2011-05-06
You will need to boot from the Windows 7 DVD and have it do the startup repair on the Windows 7 partition. If that doesn't fix it you may need to manually run check disk on it.

---

### Post by HHx66 on 2011-05-06
Well I managed to get the dual boot working in a way I can live with by tinkering around (seeing as how I had a full system image sitting safely on another drive).

I restored the Windows 7 MBR with the install DVD, then used EasyBCD and added Ubuntu to it, now when I start up I get the two options from the Windows boot loader and all is fine.

---

