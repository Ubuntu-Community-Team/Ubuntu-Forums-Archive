---
title: "Ubuntu restarts when I try to boot"
date: 2011-02-08
forum: General Help
---

### Post by jbf81tb on 2011-02-08
My computer is set up as a dual boot into windows 7 and ubuntu, but since I installed the latest updates, every time hit enter to boot into ubuntu the computer just restarts. It doesn't even go into the ubuntu grub loader like it usually does. i'm terribly confused.

---

### Post by oldfred on 2011-02-08
Was this a wubi install? Or a install to separate partitions? Were you updating Windows or Ubuntu? Is this a Dell or HP?

If not wubi have you tried reinstalling grub? or, if it is wubi you need to reinstall the windows boot loader.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Rubi1200 on 2011-02-08
If this is a Wubi install and Windows boots normally, see problem #2, solution #1 in the Wubi Megathread.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If at all unsure, post the results of the boot info script also mentioned in the main post there.

---

### Post by jbf81tb on 2011-02-08
This was a separate partition install and it's a custom built comp. I started with windows 7 home premium and later added the ubuntu partition. I'll look at the other thread and see if i get get you info on the boot. How do I reinstall the grub without getting into ubuntu. I have an ubuntu install cd, or can make one, if that helps.

---

### Post by jbf81tb on 2011-02-08
also, it was ubuntu i was updating, not windows.

---

### Post by jbf81tb on 2011-02-08
Ok, it, for some reason, let me into the grub, i booted in recovery mode, selected to "fix broken packages" and "update grub loader" then restarted and now it let me back in. The odd thing is that before i tried that I tried running my liveCD but it wouldn't load. Either way, I'm here now, and I thought I should at least provide the boot info script in case there's still something wrong and it might go haywire at any time. Also, is there an easy way to access the files on my ubuntu partition from my windows partition in case this happens again and I need to get to some critical files? Thanks so much.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,767,106   976,765,059   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       8f36bfcd-cdbe-4b0c-9980-0b7670d82c29   ext4                                     
/dev/sda1        1A3CB1193CB0F13D                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        53A9-2A15                              vfat       IOMEGA_HDD                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/IOMEGA_HDD        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1a3cb1193cb0f13d
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1a3cb1193cb0f13d
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-28-generic-pae" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1a3cb1193cb0f13d
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-28-generic-pae root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-28-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1a3cb1193cb0f13d
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-28-generic-pae root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-26-generic-pae" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1a3cb1193cb0f13d
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-26-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1a3cb1193cb0f13d
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-25-generic-pae" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1a3cb1193cb0f13d
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-25-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1a3cb1193cb0f13d
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1a3cb1193cb0f13d
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


  13.5GB: boot/grub/grub.cfg
  13.7GB: boot/initrd.img-2.6.32-25-generic-pae
  13.7GB: boot/initrd.img-2.6.32-26-generic-pae
  13.9GB: boot/initrd.img-2.6.32-28-generic-pae
  13.7GB: boot/vmlinuz-2.6.32-25-generic-pae
  13.7GB: boot/vmlinuz-2.6.32-26-generic-pae
  13.8GB: boot/vmlinuz-2.6.32-28-generic-pae
  13.9GB: initrd.img
  13.7GB: initrd.img.old
  13.8GB: vmlinuz
  13.7GB: vmlinuz.old

---

### Post by Rubi1200 on 2011-02-08
You have Wubi installed.

If both Windows and Ubuntu are now booting normally, use the Permanent Fix from the Wubi Megathread to prevent this happening again.

Please read the information there in order to understand what is going on.

If there is something not working yet, or you do not understand what needs to be done, then ask and we will help you.

---

### Post by oldfred on 2011-02-08
You have wubi not a separate partiiton install. Go back to post #3 and the link to the wubi megathread to make sure you have the fixes, so it does not happen again.

If you are using Ubuntu a lot, you may eventually want to convert to a full partition install.

From the designer of wubi.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

