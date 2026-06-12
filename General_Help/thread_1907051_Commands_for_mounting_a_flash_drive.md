---
title: "Commands for mounting a flash drive?"
date: 2012-01-10
forum: General Help
---

### Post by imachavel on 2012-01-10
so I decided to start a new thread, does anyone know the commands for mounting a flash drive? I need to install boot-repair-disk.iso to a flash drive. If I can install it, I can select to boot to it and run it at start up to try and fix grub. My grub is messed up, and if need be, I'll get back into that and create run commands for a syntax return giving grub info. 

here is what is in my flash drive so far:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0557:7000 ATEN International Co., Ltd Hub
Bus 003 Device 003: ID 03f0:0d17 Hewlett-Packard LaserJet 1012
Bus 004 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000
Bus 003 Device 004: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 001 Device 007: ID 0781:5530 SanDisk Corp. Cruzer U3 4gb SDCZ36

[FONT=monospace]sorry, those are all my usb devices, the sandisk corp cruzer u3 4gb sdcz36 is my flash drive. I am trying to list what is in the flash drive, but this isn't helping too much either:
```

sudo su
root@ubuntu:/home/ubuntu# cd /desktop/
bash: cd: /desktop/: No such file or directory
root@ubuntu:/home/ubuntu# cd Desktop/
root@ubuntu:/home/ubuntu/Desktop# mkdir flash

:confused:

Anyway, I didn't know if it was more convenient to use an existing thread or start a new one, so I just started a new one and if it's not convenient my old thread is down the page a bit. Also here is my boot script info:

Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 11 Katya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *     95,379,456   658,579,455   563,200,000  83 Linux
/dev/sda2         658,581,502   976,771,071   318,189,570   5 Extended
/dev/sda5         853,129,216   924,809,215    71,680,000  82 Linux swap / Solaris
/dev/sda6         658,581,504   776,222,719   117,641,216  83 Linux
/dev/sda7         776,224,768   781,449,215     5,224,448  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4b94c53e-8dc8-45b9-af1e-aa6f47568e1e   ext3       
/dev/sda5        f429ac74-87eb-40e9-a0cc-7ecceb923edc   swap       
/dev/sda6        8bd7df9e-99fb-40b8-99ae-5a155f67b421   ext4       
/dev/sda7        4a5c3c86-5973-4976-81de-8bf3f968aa6f   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/4b94c53e-8dc8-45b9-af1e-aa6f47568e1e ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /media/8bd7df9e-99fb-40b8-99ae-5a155f67b421 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=4b94c53e-8dc8-45b9-af1e-aa6f47568e1e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=4b94c53e-8dc8-45b9-af1e-aa6f47568e1e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=4b94c53e-8dc8-45b9-af1e-aa6f47568e1e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=4b94c53e-8dc8-45b9-af1e-aa6f47568e1e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=4b94c53e-8dc8-45b9-af1e-aa6f47568e1e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=4b94c53e-8dc8-45b9-af1e-aa6f47568e1e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=4b94c53e-8dc8-45b9-af1e-aa6f47568e1e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=4b94c53e-8dc8-45b9-af1e-aa6f47568e1e ro recovery nomodeset 
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
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 11, 2.6.38-12-generic (/dev/sda6) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8bd7df9e-99fb-40b8-99ae-5a155f67b421
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=8bd7df9e-99fb-40b8-99ae-5a155f67b421 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Linux Mint 11, 2.6.38-12-generic (/dev/sda6) -- recovery mode (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8bd7df9e-99fb-40b8-99ae-5a155f67b421
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=8bd7df9e-99fb-40b8-99ae-5a155f67b421 ro single
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Linux Mint 11, 2.6.38-8-generic (/dev/sda6) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8bd7df9e-99fb-40b8-99ae-5a155f67b421
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=8bd7df9e-99fb-40b8-99ae-5a155f67b421 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Linux Mint 11, 2.6.38-8-generic (/dev/sda6) -- recovery mode (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 8bd7df9e-99fb-40b8-99ae-5a155f67b421
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=8bd7df9e-99fb-40b8-99ae-5a155f67b421 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###



```I'll stop there that is a lot of stuff huh? Wow painful that is saved in a text file. 
[/FONT]

---

### Post by bluexrider on 2012-01-10
Oldfred and JKyleOKC gave you the information to repair your Grub and MBR in your previous postings. 

Are you still having trouble?

---

### Post by imachavel on 2012-01-10
yes I'm unsure how to install the boot-repair-disk.iso to the flash drive. This is what I'm on now. thanks for reading

---

### Post by bluexrider on 2012-01-10
[CENTER][[IMG]http://4.bp.blogspot.com/-fT9AjTaZBsE/Tfn6P5h8n_I/AAAAAAAAE7M/NZHXeZLYQVg/s400/boot-repair.png[/IMG]]("http://4.bp.blogspot.com/-fT9AjTaZBsE/Tfn6P5h8n_I/AAAAAAAAE7M/NZHXeZLYQVg/s2000/boot-repair.png")[/CENTER]

**Boot-Repair is a GUI tool to repair  various boot issues you may encounter in Ubuntu like when installing  Windows or another Linux distribution and you can't boot Ubuntu or GRUB  is not displayed anymore, some upgrade breaks GRUB, etc.**


Boot-Repair lets  you reinstall GRUB bootloader with a simple click, but there are also  some advanced options available if you want to specify the partition  where GRUB should be installed or purge and reinstall GRUB. The  application also allows you to restore the original boot sector (MBR) if  it was saved using [Clean-Ubiquity]("https://launchpad.net/%7Eyannubuntu/+archive/clean-ubiquity") (another application created by the Boot-Repair developer) and select the default OS.



You can use Boot-Repair from a regular  session, but since its supposed to repair the GRUB, you'll most  probably need to use it from a Live CD so **boot an Ubuntu Live CD and then install Boot-Repair using the commands below** (**[COLOR=red]yes, you can install it on the Live CD[/COLOR]!**):
sudo add-apt-repository ppa:yannubuntu/boot-repair sudo apt-get update sudo apt-get install boot-repair
Once installed, launch it from Dash, or if you use the classic GNOME Desktop, you'll find it under *System > Administration > Boot Repair*.

Boot-Repair is available for Ubuntu 12.04, 11.10, 11.04, 10.10 and 10.04 and it only works with GRUB 2.


I think you are going through a lot of trouble fixing your issue. The above is what I recommend.

The web site which this information came from is [B][COLOR=Red][here]("http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html")
[/COLOR][/B]
Good luck

---

### Post by imachavel on 2012-01-10
ok here is the boot script:

[http://paste.ubuntu.com/799849/](http://paste.ubuntu.com/799849/)

as it told me to do. Now I'll launch the repair and reboot and let you know what happens. Sorry meant this one:

[http://paste.ubuntu.com/799852/](http://paste.ubuntu.com/799852/)

---

### Post by imachavel on 2012-01-10
hell yeah it worked! change it to solved? I haven't tested the second partition yet but I'll try soon and if that doesn't work I guess I'll try the boot repair with the second partition as well

---

### Post by oldos2er on 2012-01-10
Changed thread title.

You can mark the thread as 'Solved' under Thread Tools at the top.

---

### Post by bluexrider on 2012-01-10
Sweet. Glad to help. Please mark this 
(SOLVED)

---

