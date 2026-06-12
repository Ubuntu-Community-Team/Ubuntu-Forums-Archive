---
title: "GRUB2 boot problems"
date: 2010-05-26
forum: General Help
---

### Post by ginx on 2010-05-26
Hello all,

I'm a noob both in the linux and the grub/grub2 worlds. I have a problem  booting into Ubuntu 10.04 in a dual boot configuration with Windows 7.

I have a Windows 7 installed on one physical HDD, and Ubuntu installed  on another.
When installing Ubuntu, I have installed grub2 in the linux partition,  leaving the windows boot loader intact. After doing that, I have  installed EasyBCD on my windows OS and added an entry in the boot menu  for Ubuntu, for chainloading grub after selecting Ubuntu in the boot  menu of Win 7.
After I select to boot into Ubuntu, the PC is stuck with the following  output on screen:
[B]Try (hd0, 0): NTFS5: No ang0
Try (hd0, 1): NTFS5: No ang0
Try (hd0, 2): invalid or null
Try (hd0, 3): invalid or null
Try (hd1, 0): Extended:
Try (hd1, 1): Ext2:

[/B]
[LIST]
[*]After some search on the web, I have tried one solution of assigning the hidden partition of Win 7 (system partition) a drive letter. That didn't change the behavior of grub.
[*] I'm not sure about he meaning of the last entry (telling something about ext2), but I have installed Ubuntu using Ext4.
[/LIST]
I would appreciate your help and advice as I'm eager to start using Ubuntu.
 

Thanks,

---

### Post by ginx on 2010-05-29
Can anyone give me some direction for fixing the problem. I really want to start using Ubuntu...

---

### Post by ginx on 2010-06-01
One thing that I found out. When I set the HDD on which I installed Ubuntu (and grub) to act as a master, grub loads Ubuntu as expected.

---

### Post by Ams1221 on 2010-07-26
I have the exact same problem, could anybody be of assistance?

---

### Post by prodigy_ on 2010-07-26
Boot from LiveCD, run the Boot Info Script from my sig and post the results here.

---

### Post by Ams1221 on 2010-07-26
> **prodigy_ said:**
> Boot from LiveCD, run the Boot Info Script from my sig and post the results here.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   488,394,751   488,187,904   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         582,174,720   621,236,223    39,061,504  83 Linux
/dev/sdb2    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb3             206,848   582,173,644   581,966,797   7 HPFS/NTFS
/dev/sdb4         621,238,270   625,139,711     3,901,442   5 Extended
/dev/sdb5         621,238,272   625,139,711     3,901,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        CED6612CD661164D                       ntfs       System Reserved               
/dev/sda2        BE2269B222696FF7                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9be3ca6f-723b-4d13-91a4-f57bffca3d5d   ext4                                     
/dev/sdb2        10BAA372BAA35350                       ntfs       System Reserved               
/dev/sdb3        704CB3E14CB39FF0                       ntfs                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        63632907-b2d2-468b-974f-63f852961080   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 9be3ca6f-723b-4d13-91a4-f57bffca3d5d
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 9be3ca6f-723b-4d13-91a4-f57bffca3d5d
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9be3ca6f-723b-4d13-91a4-f57bffca3d5d
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=9be3ca6f-723b-4d13-91a4-f57bffca3d5d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9be3ca6f-723b-4d13-91a4-f57bffca3d5d
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=9be3ca6f-723b-4d13-91a4-f57bffca3d5d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9be3ca6f-723b-4d13-91a4-f57bffca3d5d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9be3ca6f-723b-4d13-91a4-f57bffca3d5d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ced6612cd661164d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 10baa372baa35350
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=9be3ca6f-723b-4d13-91a4-f57bffca3d5d /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 315.4GB: boot/grub/core.img
 311.5GB: boot/grub/grub.cfg
 315.8GB: boot/initrd.img-2.6.32-24-generic-pae
 315.7GB: boot/vmlinuz-2.6.32-24-generic-pae
 315.8GB: initrd.img
 315.7GB: vmlinuz
```

---

### Post by prodigy_ on 2010-07-26
> Grub 2 is installed in the MBR of /dev/sdb
**/dev/sdb** is your 320GB drive. Have you tried to select it as the boot device in BIOS?

---

### Post by Ams1221 on 2010-07-26
> **prodigy_ said:**
> **/dev/sdb2** is your 320GB drive. Have you tried to select it as the boot device in BIOS?

i missread your post.

I did not try that, because i would like to dual boot using easybcd.

---

### Post by -kg- on 2010-07-26
Do you have EasyBCD Version 2.0.1 (the latest) installed, or an earlier version?  According to [this site]("http://neosmart.net/blog/2010/welcome-to-easybcd-2/"):

> Support for GRUB2 and ext4fs (we're looking at you, Ubuntu *glare*)

Yeah, yeah...just because Ubuntu is cutting edge... :D

If you don't have the latest installed, then you might want to download and install the latest.  I did notice in the forums that there were a few issues earlier.

---

