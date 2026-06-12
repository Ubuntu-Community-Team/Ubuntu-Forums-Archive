---
title: "Xubuntu not booting desktop"
date: 2011-03-01
forum: General Help
---

### Post by Veld on 2011-03-01
Hi, can anyone help me out? Ubuntu doesn't load. While booting, it displays an error message saying some of the lists in ipblock couldn't be loaded, followed by a red-coloured "[fail]". Then, the screen goes black and shows nothing more.
So, how do I stop ipblock from starting at startup (from the command line)? Thanks in advance!

---

### Post by Veld on 2011-03-02
...anyone?

Edit: I read around here that I can stop ipblock it from autostarting by changing the value of AUTOSTART to "no" inside ipblock.conf. My question is: how do I open (from the command line) the file so I can edit it?

---

### Post by seawolf167 on 2011-03-02
> **Veld said:**
> Edit: I read around here that I can stop ipblock it from autostarting by changing the value of AUTOSTART to "no" inside ipblock.conf. My question is: how do I open (from the command line) the file so I can edit it?

You can use **vi**, though it may be a [little confusing]("http://www.google.com/url?sa=t&source=web&cd=2&sqi=2&ved=0CCUQFjAB&url=http%3A%2F%2Fwww2.cs.uidaho.edu%2F%7Erinker%2Fed03.pdf&rct=j&q=vi%20cheat%20sheet&ei=yfVuTZ3PK8iXOvTg7P0I&usg=AFQjCNESZWpSIxO0Ttca_6IqWeiU6AyFgA&cad=rja") the first time you use it

```
vi /path/to/file.extension
```

If it says that its open in read-only mode or is unable to save, then you'll need a sudo in front of the above command

```
sudo vi /path/to/file.extension
```

You can also use **nano**, which will be much easier for you to edit without reading a cheat sheet

```
nano /path/to/file.extension
```

---

### Post by Veld on 2011-03-03
Thanks, man. With nano I was able to edit the ipblock.conf file and set the AUTOSTART value to "no", but Xubuntu still wouldn't boot. I then tried to eliminate all the lists from the ipblock.lists, thinking that perhaps the problem could be solved by eliminating all the lists which couldn't be loaded. Xubuntu still doesn't boot. 
I don't event know if the problem is being caused by ipblock anymore :\

---

### Post by seawolf167 on 2011-03-03
What if you remove IPBlock and then reboot, see if you get the same message?

```
sudo apt-get purge ipblock
```

I'm not sure if ipblock is the correct package name, but if it isn't, insert the correct one.

---

### Post by leviathan8 on 2011-03-03
> **seawolf167 said:**
> What if you remove IPBlock and then reboot, see if you get the same message?

```
sudo apt-get purge ipblock
```I'm not sure if ipblock is the correct package name, but if it isn't, insert the correct one.

I think he means iptables, not ipblock.

---

### Post by Veld on 2011-03-03
I've removed iptables (ipblock is the frontend), but the system still doesn't boot. The screen just goes black. How can I find out what's wrong?

Edit: I remember updating before this happened. Perhaps it's related?

Edit 2: I booted using the Live CD and ran Boot Info Script. Here's what I got:

> 
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
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

/dev/sda1    *             63   388,311,243   388,311,181   7 HPFS/NTFS
/dev/sda2         388,313,086 1,953,523,711 1,565,210,626   5 Extended
/dev/sda5         388,313,088 1,931,270,143 1,542,957,056  83 Linux
/dev/sda6       1,931,272,192 1,953,523,711    22,251,520  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,849,447     7,849,386   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9A90F49790F47AD9                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2e900421-28b4-486d-8430-f255cc09f5de   ext4                                     
/dev/sda6        c97823f8-71db-4240-980d-39c4e8a29a70   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9C76-0A1A                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer /noguiboot 

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
search --no-floppy --fs-uuid --set 2e900421-28b4-486d-8430-f255cc09f5de
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 2e900421-28b4-486d-8430-f255cc09f5de
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
    search --no-floppy --fs-uuid --set 2e900421-28b4-486d-8430-f255cc09f5de
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=2e900421-28b4-486d-8430-f255cc09f5de ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2e900421-28b4-486d-8430-f255cc09f5de
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=2e900421-28b4-486d-8430-f255cc09f5de ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2e900421-28b4-486d-8430-f255cc09f5de
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2e900421-28b4-486d-8430-f255cc09f5de ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2e900421-28b4-486d-8430-f255cc09f5de
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2e900421-28b4-486d-8430-f255cc09f5de ro single 
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
    search --no-floppy --fs-uuid --set 2e900421-28b4-486d-8430-f255cc09f5de
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2e900421-28b4-486d-8430-f255cc09f5de
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9a90f49790f47ad9
    drivemap -s (hd0) ${root}
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
UUID=2e900421-28b4-486d-8430-f255cc09f5de /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c97823f8-71db-4240-980d-39c4e8a29a70 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 954.8GB: boot/grub/core.img
 847.6GB: boot/grub/grub.cfg
 200.0GB: boot/initrd.img-2.6.35-22-generic
 230.5GB: boot/initrd.img-2.6.35-25-generic
 954.8GB: boot/vmlinuz-2.6.35-22-generic
 954.8GB: boot/vmlinuz-2.6.35-25-generic
 230.5GB: initrd.img
 200.0GB: initrd.img.old
 954.8GB: vmlinuz
 954.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 


Is there anything wrong?

---

### Post by sikander3786 on 2011-03-04
@ Veld:

The boot script output looks pretty ok to me. There are no problems. What you can try at first to solve the blank screen problem is to try the 'nomodeset' boot parameter.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

If that doesn't solve the issue, try purging and re-installing Grub from a Live CD.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If there are any error messages during boot, you need to post the exact messages please.

---

### Post by Veld on 2011-03-04
nomodeset did not solve this issue. I'll try to reinstall GRUB tonight (it won't mess up with the dual boot, I hope?). 
I used to see only one error message regarding IPBlock, but it doesn't show up anymore as I purged iptables. Now the screen is just... black. No errors, nothing.

---

### Post by Veld on 2011-03-05
I gave up and just formatted the disk. Problem solved.

---

