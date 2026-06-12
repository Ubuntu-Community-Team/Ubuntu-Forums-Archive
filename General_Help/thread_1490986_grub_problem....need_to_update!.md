---
title: "grub problem....need to update!"
date: 2010-05-23
forum: General Help
---

### Post by amite on 2010-05-23
i am using ubuntu 9.10(grub 1.97~beta).i had double boot with windows 7 and ubuntu 9.10.
Now i  installed CentOS 5.5 and during installation skip grub installation.now i cant boot to CentOS as there is no option for it in boot table.I found some tutorial on internet already for grub editing but all those use menu.lst which i think not available with grub2.So please instruct me how to edit grub file ..........
here is part of my current entry for grub.cfg
> 

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 12bb7875-734b-487f-ade3-c87e1ac0eae7
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=12bb7875-734b-487f-ade3-c87e1ac0eae7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 12bb7875-734b-487f-ade3-c87e1ac0eae7
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=12bb7875-734b-487f-ade3-c87e1ac0eae7 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 12bb7875-734b-487f-ade3-c87e1ac0eae7
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=12bb7875-734b-487f-ade3-c87e1ac0eae7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 12bb7875-734b-487f-ade3-c87e1ac0eae7
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=12bb7875-734b-487f-ade3-c87e1ac0eae7 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 80e45aeae45ae1c8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
i have installed centos on sda9.

---

### Post by Elfy on 2010-05-23
Have you run sudo update-grub

It should find then centos install and add it.

Edit - if it finds centos, adds it to grub but then centos does not boot please repost the new grub.cfg

---

### Post by amite on 2010-05-23
Thanks!
after sudo update-grub ,boot entry shows centos.
grub.cfg entry  is as
> 

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 80e45aeae45ae1c8
    chainloader +1
}
menuentry "CentOS release 5.5 (Final) (on /dev/sda9)" {
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 0c151ca5-f609-4a32-b460-88cbb599b0d1
    linux /boot/vmlinuz-2.6.18-194.el5 root=/dev/sda9
}


But when i try to boot centos it shows following error :
**kernel panic- not syncing :VFS : unable to mount root fs on unknown block(0,0)**

---

### Post by amite on 2010-05-24
Any1 plz ........
Now centos is in boot list but booting it gives following lines......
[B]kernel panic- not syncing :VFS : unable to mount root fs on unknown block(0,0)


[/B]

---

### Post by Elfy on 2010-05-24
If Centos has a initrd then it is missing from the grub stanza. 

Try adding this to the custom folder

> menuentry "Centos"{
set root=(hd0,9)
chainloader +1
}

```
gksudo gedit /etc/grub.d/40_custom
```

```
sudo update-grub
```

---

### Post by amite on 2010-05-24
i added these lines to the end of  40_custom 
>  	 	 		 			 				menuentry "Centos"{
set root=(hd0,9)
chainloader +1
}

and then update grub,but it didn't added any new entry to the boot list and also booting with centos is giving same problem

---

### Post by Elfy on 2010-05-24
> **amite said:**
> i added these lines to the end of  40_custom 

and then update grub,but it didn't added any new entry to the boot list and also booting with centos is giving same problem

It doesn't show in grub-update - but it should have added it.

Can you post your grub.cfg and fdisk

```
cat /boot/grub/grub.cfg
sudo fdisk -l
```

Please use code tags.

---

### Post by amite on 2010-05-24
> $ sudo fdisk -l
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4980    40001818+  83  Linux
/dev/sda2            4981        4993      102400    7  HPFS/NTFS
/dev/sda3            4993       12172    57660416    7  HPFS/NTFS
/dev/sda4           12172       30401   146429633    f  W95 Ext'd (LBA)
/dev/sda5           14913       17653    22014976    7  HPFS/NTFS
/dev/sda6           17654       24028    51200000    7  HPFS/NTFS
/dev/sda7           24028       30076    48579768    7  HPFS/NTFS
/dev/sda8           30077       30401     2610531   82  Linux swap / Solaris
/dev/sda9   *       12172       14912    22013952   83  Linux

Partition table entries are not in disk order



grub.cfg
> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 12bb7875-734b-487f-ade3-c87e1ac0eae7
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 12bb7875-734b-487f-ade3-c87e1ac0eae7
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=12bb7875-734b-487f-ade3-c87e1ac0eae7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 12bb7875-734b-487f-ade3-c87e1ac0eae7
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=12bb7875-734b-487f-ade3-c87e1ac0eae7 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 12bb7875-734b-487f-ade3-c87e1ac0eae7
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=12bb7875-734b-487f-ade3-c87e1ac0eae7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 12bb7875-734b-487f-ade3-c87e1ac0eae7
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=12bb7875-734b-487f-ade3-c87e1ac0eae7 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 80e45aeae45ae1c8
    chainloader +1
}
menuentry "CentOS release 5.5 (Final) (on /dev/sda9)" {
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 0c151ca5-f609-4a32-b460-88cbb599b0d1
    linux /boot/vmlinuz-2.6.18-194.el5 root=/dev/sda9
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Centos"{
set root=(hd0,9)
chainloader +1
} 
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom.copy ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom.copy ###

---

### Post by Elfy on 2010-05-24
All looks ok to me. Possibly you need to install grub for centos - not sure how to do so as I've not used the OS.

---

### Post by oldfred on 2010-05-24
For the chainboot entry to work you have to have installed the Centos boot loader to sda9. Does it use grub or grub2?

---

