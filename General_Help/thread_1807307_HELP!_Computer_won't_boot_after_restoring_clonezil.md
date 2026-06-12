---
title: "HELP! Computer won't boot after restoring clonezilla image"
date: 2011-07-18
forum: General Help
---

### Post by josephellengar on 2011-07-18
Hi. I have long been using clonezilla as my backup/restore software and have never had a problem with it before, ever. Today I backed up my entire disk (windows 7 and Ubuntu 10.10) and upgraded to 11.04 to try it out. I didn't like it, so I decided to restore the backup. Now I can't boot my computer. It gets to a black screen and nothing happens. No error message, nothing. I can still boot from a live USB (which is what I am using now), and I can also boot from a Windows Live CD. I tried using the MBR repair on Windows and reinstalling Grub through the Ubuntu Live USB. Neither of them have worked. Do you have any ideas what the problem might be? Any help would be greatly appreciated! Thank you!

---

### Post by garvinrick4 on 2011-07-18
Can you chroot into Ubuntu install and install grub from there.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")
I would have no idea what you have in mbr right now. You dist-upgraded so I would
imagine it is looking for something that is not there.

What about boot script can you run it that would tell story:
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by josephellengar on 2011-07-19
> **garvinrick4 said:**
> Can you chroot into Ubuntu install and install grub from there.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")
I would have no idea what you have in mbr right now. You dist-upgraded so I would
imagine it is looking for something that is not there.

What about boot script can you run it that would tell story:
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

Thank you so much for the prompt reply. Chrooting into Ubuntu didn't help, but I ran boot info script. This gave quite a lot of output. I'm not sure what to make of it, but perhaps you could look at it? Thank you so much for your help. I really don't want to have to reinstall two operating systems. I ran this from a live USB Ubuntu. Oh, and just so you know, /dev/sdc is a multiboot flash drive, which is why it has the horrendously long Grub menu. That has Grub 4 Windows on it and is not part of the problem.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

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
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.85 2010-02-20
    Boot sector info:   Syslinux looks at sector 32776 of /dev/sdc1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /menu.lst /syslinux.cfg /grub.exe /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   157,870,079   157,460,480   7 NTFS / exFAT / HPFS
/dev/sda3         157,870,755   312,576,704   154,705,950   5 Extended
/dev/sda5         157,870,818   262,731,775   104,860,958  83 Linux
/dev/sda6         262,743,138   312,576,704    49,833,567  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   597,457,349   597,457,287   7 NTFS / exFAT / HPFS
/dev/sdb2         597,457,350   625,137,344    27,679,995  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8005 MB, 8005787648 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15636304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    15,631,244    15,631,182   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              iso9660    Ubuntu 10.04 LTS i386
/dev/loop1                                              squashfs   
/dev/sda1        40389FB8389FAB82                       ntfs       SYSTEM
/dev/sda2        645684D25684A700                       ntfs       OS
/dev/sda5        098c0e33-2ea8-420a-a7c9-2bcdc9011118   ext4       
/dev/sda6        c835dec7-b978-4793-b23d-2f812c6a1f96   ext4       home
/dev/sdb1        74912E3D2459A0BE                       ntfs       
/dev/sdb2        0de4ba0c-7406-4974-a25b-a1d10f68be39   swap       
/dev/sdc1        94E4-7D13                              vfat       TOOLKIT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /isodevice               vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 098c0e33-2ea8-420a-a7c9-2bcdc9011118
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 098c0e33-2ea8-420a-a7c9-2bcdc9011118
insmod png
if background_image /boot/grub/grub-splash-wide.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=blue/green
  set menu_color_highlight=green/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 098c0e33-2ea8-420a-a7c9-2bcdc9011118
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 098c0e33-2ea8-420a-a7c9-2bcdc9011118
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 098c0e33-2ea8-420a-a7c9-2bcdc9011118
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 098c0e33-2ea8-420a-a7c9-2bcdc9011118
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 40389FB8389FAB82
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 645684D25684A700
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0

# root filesystem
UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 / ext4 errors=remount-ro,discard 0 1

# swap file
UUID=0de4ba0c-7406-4974-a25b-a1d10f68be39 none swap sw 0 0

# home
/dev/sda6 /home ext4 errors=remount-ro,discard 0 1

# storage
/dev/sdb1 /home/ross/storage ntfs-3g auto,exec,user,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0

# flash drive
/dev/sdc1 /home/ross/flash vfat iocharset=utf8,umask=000,user,noauto,exec 0 0

#tmpfs
tmpfs /tmp tmpfs defaults,noatime 0 0
tmpfs /var/tmp tmpfs defaults,noatime 0 0
tmpfs /usr/src tmpfs defaults,noatime 0 0
tmpfs /var/cache/apt/archives tmpfs defaults,noatime 0 0
tmpfs /var/log tmpfs defaults,noatime 0 0


--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  75.502636909 = 81.070339072   boot/grub/core.img                             1
  91.798214912 = 98.567582720   boot/grub/grub.cfg                             1
  84.442734718 = 90.669696000   boot/initrd.img-2.6.32-25-generic              2
  83.790524483 = 89.969390592   boot/initrd.img-2.6.35-22-generic              2
  87.532505989 = 93.987312640   boot/vmlinuz-2.6.32-25-generic                 1
  87.344235420 = 93.785158656   boot/vmlinuz-2.6.35-22-generic                 1
  83.790524483 = 89.969390592   initrd.img.old                                 2
  87.344235420 = 93.785158656   vmlinuz.old                                    1

================================ sdc1/menu.lst: ================================

--------------------------------------------------------------------------------
#default 0 
#timeout 30 
color NORMAL HIGHLIGHT HELPTEXT HEADING 
splashimage=(hd0,0)/splash.xpm.gz 
foreground=000000 
background=FFFFFF 
 
title AVG Rescue CD 100.100826 (Anti-Virus + Anti-Spyware) 
find --set-root /avg.iso 
map /avg.iso (hd32) 
map --hook 
chainloader (hd32) 
 
title Balder DOS 10 
map --unsafe-boot /balder10.img (fd0) 
map --hook 
chainloader --force (fd0)+1 
rootnoverify (fd0) 
 
title BitDefender Rescue CD 8/6/10 (Virus Scanner) 
find --set-root /bitdefender-rescue-cd.iso 
map /bitdefender-rescue-cd.iso (0xff) 
map --hook 
root (0xff) 
kernel /casper/vmlinuz boot=casper iso-scan/filename=/bitdefender-rescue-cd.iso 
initrd /casper/initrd.gz 
 
title Clonezilla 20100921 (Alternative) 
find --set-root /clonezilla/live/initrd1.img 
kernel /clonezilla/live/vmlinuz1 boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run='ocs-live-general' ocs_live_extra_param='' ocs_live_keymap='' ocs_live_batch='no' ocs_lang='' vga=788 ip=frommedia nosplash live-media-path=/clonezilla/live toram=filesystem.squashfs 
initrd /clonezilla/live/initrd1.img 
 
title Gparted 0.6.4-1  
find --set-root /gparted/live/initrd1.img 
kernel /gparted/live/vmlinuz1 boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run='ocs-live-general' ocs_live_extra_param='' ocs_live_keymap='' ocs_live_batch='no' ocs_lang='' vga=788 ip=frommedia nosplash live-media-path=/gparted/live toram=filesystem.squashfs 
initrd /gparted/live/initrd1.img 
 
title DBAN 1.0.7 (Drive Nuker) 
find --set-root /dban-1.0.7_i386.iso 
map --mem /dban-1.0.7_i386.iso (hd32) 
map --hook 
root (hd32) 
chainloader (hd32) 
 
title DSL 4.4.10 
find --set-root /dsl-4.4.10-initrd.iso 
map --mem /dsl-4.4.10-initrd.iso (hd32) 
map --hook 
root (hd32) 
chainloader (hd32) 
 
title Kaspersky Rescue CD 10.0.21.5 (Virus Scanner) 
find --set-root /rescue/rescue.iso 
map /rescue/rescue.iso (0xff) 
map --hook 
root (0xff) 
chainloader (0xff) 
 
title Linux OS from the Internet 
kernel /gpxe.lkrn 
 
title Memtest86+ 3.5 
find --set-root /memtest86+-4.00.iso 
map --mem /memtest86+-4.00.iso (hd32) 
map --hook 
root (hd32) 
chainloader (hd32) 
 
title NT Password & Registy Editor 080802 
find --set-root /cd080802.iso 
map /cd080802.iso  (hd32) 
map --hook 
chainloader (hd32) 
 
title OphCrack 3.3.1 
kernel /ophcrack/boot/bzImage rw root=/dev/null vga=normal lang=C kmap=us screen=1024x768x16 autologin 
initrd /ophcrack/boot/rootfs.gz  
 
title Parted Magic 4.10 
find --set-root /pmagic-4.10.iso 
map /pmagic-4.10.iso (hd32) 
map --hook 
root (hd32) 
chainloader (hd32) 
 
title Puppy Linux 4.3.1 
find --set-root /puppy/pup-431.sfs 
kernel /puppy/vmlinuz 
initrd /puppy/initrd.gz 
 
title Redo Backup and Recovery 
find --set-root --ignore-floppies --ignore-cd /redobackup.iso 
map --heads=0 --sectors-per-track=0 /redobackup.iso (hd32) 
map --hook 
chainloader (hd32) 
 
title Spinrite 6.0 
map --mem /SpinRite.img (fd0) 
map --hook 
chainloader (fd0)+1 
rootnoverify (fd0) 
 
title TinyCore 2.11.3 
find --set-root /tinycore_2.11.3.iso 
map /tinycore_2.11.3.iso (0xff) || map --mem /tinycore_2.11.3.iso (0xff) 
map --hook 
chainloader (0xff) 
 
title Ubuntu 10.04 32 bit 
find --set-root /ubuntu-10.04-desktop-i386.iso 
map /ubuntu-10.04-desktop-i386.iso (0xff) 
map --hook 
root (0xff) 
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-10.04-desktop-i386.iso splash 
initrd /casper/initrd.lz 
 
title Ubuntu 10.04 64 bit 
find --set-root /ubuntu-10.04-desktop-amd64.iso 
map /ubuntu-10.04-desktop-amd64.iso (0xff) 
map --hook 
root (0xff) 
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-10.04-desktop-amd64.iso splash 
initrd /casper/initrd.lz 
 
title Ultimate Boot CD 5.0.1 
find --set-root /ubcd501.iso 
map /ubcd501.iso (hd32) 
map --hook 
chainloader (hd32) 
 
title Boot From Hard Drive 
map (hd0) (hd1) 
map (hd1) (hd0) 
map --hook 
chainloader (hd0)+1 
rootnoverify (hd0) 
 
title Grub4Dos Command Line 
commandline 
 
title Reboot 
reboot 
 
 
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default grub
LABEL grub
KERNEL grub.exe--------------------------------------------------------------------------------

========================= sdc1/grub.exe embedded menu: =========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1

title find /menu.lst, /boot/grub/menu.lst, /grub/menu.lst
    errorcheck off
    configfile /menu.lst
    configfile /boot/grub/menu.lst
    configfile /grub/menu.lst
    find --set-root --ignore-floppies --ignore-cd /menu.lst && configfile /menu.lst
    find --set-root --ignore-floppies --ignore-cd /boot/grub/menu.lst && configfile /boot/grub/menu.lst
    find --set-root --ignore-floppies --ignore-cd /grub/menu.lst && configfile /grub/menu.lst
    errorcheck on
    commandline

title commandline
    commandline

title reboot
    reboot

title halt
    halt


--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux.cfg                                   1


```

---

### Post by garvinrick4 on 2011-07-19
In live Cd or USB copy and paste these in a terminal:
```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo chroot /mnt
```
```
grub-install /dev/sda
```
```
update-grub

 
```
```
exit
```
   	 	 	 	 	 	  ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
```
```
sudo reboot
```

---

### Post by josephellengar on 2011-07-19
> **garvinrick4 said:**
> In live Cd or USB copy and paste these in a terminal:
```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo chroot /mnt
```
```
grub-install /dev/sda
```
```
update-grub

 
```
```
exit
```
   	 	 	 	 	 	  ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
```
```
sudo reboot
```

Man, you are a lifesaver! Thank you thank you thank you! It all works. So, was the problem just that grub wasn't installed? I did install grub but I guess I forgot to update it?

THANK YOU!!!!!!!

---

### Post by garvinrick4 on 2011-07-19
> So, was the problem just that grub wasn't installed?
There are quite a few ways to install grub into the "mbr" of a drive.
When all else fails the chroot way is the way to go. You can install and update
from inside root and actually see when grub updated if all installs are there
without rebooting. I used this way because of the drive being cloned might have
worked with much less code as such below:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo reboot
Go into ubuntu install and:
sudo update-grub
  
#But again if all else fails use the chroot method because you are then working from inside
the install: This thread below has another way to chroot that uses less code but accomplishing the same task. Enjoy your Ubuntu.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by npr77 on 2012-10-22
> **garvinrick4 said:**
> In live Cd or USB copy and paste these in a terminal:
```
sudo mount ...
```

Thank you garvinrick4, this was very helpful! I have to figure out how to clone my partitions without destroying the grup installation (I have to try expert mode -g). Thanks to your hint I learned something new (the chroot command) and fixed my computer. Awesome :)

Regards
Nick

---

### Post by wildmanne39 on 2012-10-22
Old thread closed.

---

