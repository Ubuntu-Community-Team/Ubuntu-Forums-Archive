---
title: "Help Ubuntu won't load!"
date: 2011-02-16
forum: General Help
---

### Post by Visvalor on 2011-02-16
I'm new to Linux so I have no idea what I'm really doing. Anyways after the latest update about an hour or so ago, my computer insisted I restart. When I did, it just loads to a desktop (Wallpaper picture), a mouse pointer and nothing else. The little circle (Windows Hourglass Equal) keeps loading repeatedly on and off and I presume processing something in a loop. But it never loads to anything past that.

I've tried logging to recovery and followed a few procedures online suggested to help with linux boots such as

"sudo dpkg-reconfigure xserver-xorg"

If it helps, I've recently installed Oblivion with wine, but never ran it. Before that, I installed Imagescan! for Linux. Other than that, haven't installed anything.

Also if it helps, the screensaver works. But that's it

---

### Post by sanderd17 on 2011-02-16
does your processor keeps running?

press CTRK+ALT+F1, you will get into a terminal mode and you will need to log in.

there you can run the command
```

top

```

to see if special processes are active or not. please report it if you see anything weird. you have to return to the GUI with CTRL+ALT+F7

---

### Post by wilee-nilee on 2011-02-16
If you hold down the shift key as soon as you power on it will show the grub menu, try a lower kernel. I have to assume a lot here you don't mention what you actually have installed ie which Ubuntu, and if your dual booting.

---

### Post by Visvalor on 2011-02-16
It's stuck in a loop that looks something like this

[ 595 and changing numbers ata1.00: status: [DRDY ERR }
Same as above then;

error: { UNC }
exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
BMDMA stat 0x64
failed command: READ DMA EXT
cmd 25/00:08:00:1c:04/00:00:60:00:00:/e0 tag 0 dmg 4096 in
res 51/40:00:00:1c:04/40:00:60:00:00/e0 Emask ox9 (media error)
status: { DRDY ERR }
error: {UNC }
exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
BMDMA stat 0x64
failed command: READ DMA EXT
cmd (same stuff as above pretty much)

At the end it says I/O error, dev sda, sector 1610882048


From my guess, it's a hard drive failure...?

---

### Post by Visvalor on 2011-02-16
Also if it helps, Ubuntu 10.10. Not dual booted. Installed directly on a 1tb HD with a 2tb backup. AMD Phenom 2.4ghz, 4gb ram

---

### Post by wilee-nilee on 2011-02-16
So if you can't get to the grub menu with the shift key you might try this, it will give a what is where look at your setup.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Visvalor on 2011-02-16
Done. Here you go. Thanks for the help so far.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *  1,945,522,176 1,953,523,711     8,001,536  82 Linux swap / Solaris
/dev/sda2               2,046 1,945,522,175 1,945,520,130   5 Extended
/dev/sda5               2,048 1,945,522,175 1,945,520,128  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 3,907,024,064 3,907,024,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             48     7,831,551     7,831,504   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        54e697c5-e487-4316-8859-618dd62f3452   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3c9918e6-0e9b-4af9-8544-fd39cab1072e   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6a910336-436e-469a-b3ef-588b504e3e54   ext4       Hauss                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        B345-5CB9                              vfat       Lexar                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/3c9918e6-0e9b-4af9-8544-fd39cab1072e ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 3c9918e6-0e9b-4af9-8544-fd39cab1072e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3c9918e6-0e9b-4af9-8544-fd39cab1072e
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3c9918e6-0e9b-4af9-8544-fd39cab1072e
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=3c9918e6-0e9b-4af9-8544-fd39cab1072e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3c9918e6-0e9b-4af9-8544-fd39cab1072e
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=3c9918e6-0e9b-4af9-8544-fd39cab1072e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3c9918e6-0e9b-4af9-8544-fd39cab1072e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3c9918e6-0e9b-4af9-8544-fd39cab1072e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3c9918e6-0e9b-4af9-8544-fd39cab1072e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3c9918e6-0e9b-4af9-8544-fd39cab1072e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3c9918e6-0e9b-4af9-8544-fd39cab1072e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3c9918e6-0e9b-4af9-8544-fd39cab1072e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
UUID=3c9918e6-0e9b-4af9-8544-fd39cab1072e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=54e697c5-e487-4316-8859-618dd62f3452 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  51.6GB: boot/grub/core.img
 824.8GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.35-22-generic
   9.1GB: boot/initrd.img-2.6.35-25-generic
  51.6GB: boot/vmlinuz-2.6.35-22-generic
  51.6GB: boot/vmlinuz-2.6.35-25-generic
   9.1GB: initrd.img
   1.4GB: initrd.img.old
  51.6GB: vmlinuz
  51.6GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2011-02-16
I'm not seeing any anomalies in the script, we might wait for more help.

I suggested getting to the grub menu twice, but you have not responded. Have you tried the shift at powering on and another kernel?

---

### Post by Visvalor on 2011-02-16
Yes I've used shift to get to grub many times, and I've tried both Kernals and both just hang 

When you hit ctrl+alt+f1 and see what's going on, it's just looping this forever;

[ 595 and changing numbers ata1.00: status: [DRDY ERR }
Same as above then;

error: { UNC }
exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
BMDMA stat 0x64
failed command: READ DMA EXT
cmd 25/00:08:00:1c:04/00:00:60:00:00:/e0 tag 0 dmg 4096 in
res 51/40:00:00:1c:04/40:00:60:00:00/e0 Emask ox9 (media error)
status: { DRDY ERR }
error: {UNC }
exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
BMDMA stat 0x64
failed command: READ DMA EXT
cmd (same stuff as above pretty much)

At the end it says I/O error, dev sda, sector 1610882048

---

### Post by sanderd17 on 2011-02-17
maybe a bad secotor, can you do a fsck from inside GRUB or using a live CD?

---

