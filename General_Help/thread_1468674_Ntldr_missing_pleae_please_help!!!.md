---
title: "Ntldr missing pleae please help!!!"
date: 2010-05-01
forum: General Help
---

### Post by supermeip on 2010-05-01
i am brand new to Ubuntu and i tried to dual boot  winxp and unbuntu 10.04 and the first time failed so i had to reinstall Ubuntu both times thouh i got an error when trying to boot xp that said NTLDR is missing press ctrl alt deleat to restart and now i cant acces windows can someone pls help me! also im a super nube so really low tech talk pls

---

### Post by yozgoesdigital on 2010-05-01
First of all most probably it can be repaired easily

NTLDR is the booting program for windows. If you search for ntldr in a search engine you will see plenty of solutions to reinstall it. By head it looks like this:
load the win cd-rom--> start the repairing console (pressing r) --> use command FIXBOOT

But be warned!!! I do not know what it would do with your current grub installation. (this depends on your hard disk configuration)

If you want more info you should probably post the result of the following command in the terminal:
```
sudo fdisk -l
```

Hope this helps or at least comforts you that the problem is solvable!

---

### Post by supermeip on 2010-05-01
> **yozgoesdigital said:**
> First of all most probably it can be repaired easily

NTLDR is the booting program for windows. If you search for ntldr in a search engine you will see plenty of solutions to reinstall it. By head it looks like this:
load the win cd-rom--> start the repairing console (pressing r) --> use command FIXBOOT

But be warned!!! I do not know what it would do with your current grub installation. (this depends on your hard disk configuration)

If you want more info you should probably post the result of the following command in the terminal:
```
sudo fdisk -l
```Hope this helps or at least comforts you that the problem is solvable!


and i dont have a cd lost it a long time ago
```
supermeip@supermeip:~$ sudo fdisk -l
[sudo] password for supermeip: 

Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c213995

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          25       10506    84196665    7  HPFS/NTFS
/dev/sda2           10507       11889    11108947+   7  HPFS/NTFS
/dev/sda3           11890       11898       66340    7  HPFS/NTFS
/dev/sda4           11898       14597    21681153    5  Extended
/dev/sda5           13084       14527    11588608   83  Linux
/dev/sda6           14527       14597      560128   82  Linux swap / Solaris
/dev/sda7           11898       13028     9074688   83  Linux
/dev/sda8           13028       13083      448512   82  Linux swap / Solaris

Partition table entries are not in disk order
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
84 heads, 62 sectors/track, 7502 cylinders
Units = cylinders of 5208 * 2048 = 10665984 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      128394    0  Empty
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/sdb2              13        7503    78022222    b  W95 FAT32
supermeip@supermeip:~$ 
```

---

### Post by spuny on 2010-05-01
I think you can fix that by inserting XP disc, after you boot from cd click on repair, and that should fix it! Also try f8, keep clicking on f8 after your main screens load then a black screen will appear choose from it last good known configuration. But I'm not sure if any of those will affect the GRUB loader.

Check this link it might help
" [http://www.computerhope.com/issues/ch000465.htm#b](http://www.computerhope.com/issues/ch000465.htm#b) "

---

### Post by supermeip on 2010-05-01
> **spuny said:**
> I think you can fix that by inserting XP disc, after you boot from cd click on repair, and that should fix it! Also try f8, keep clicking on f8 after your main screens load then a black screen will appear choose from it last good known configuration. But I'm not sure if any of those will affect the GRUB loader.

Check this link it might help
" [http://www.computerhope.com/issues/ch000465.htm#b](http://www.computerhope.com/issues/ch000465.htm#b) "

i said i dont have the disk!

---

### Post by supermeip on 2010-05-01
is there a way to boot windows from within Ubuntu?

---

### Post by spuny on 2010-05-01
did you try last good known configuration? And I will try to get you the NTLDR files

---

### Post by spuny on 2010-05-01
I've attached you NTLDR file & NTDETECT, I will assume that you have windows on drive c:\ .. so boot in linux then mount(double click the partition name) which contains your windows files then copy those files in your main windows drive c:\. Hope this works.

---

### Post by supermeip on 2010-05-01
> **spuny said:**
> I've attached you NTLDR file & NTDETECT, I will assume that you have windows on drive c:\ .. so boot in linux then mount your windows drive then copy those files in your main windows drive. Hope this works.
how do you mount the drive

---

### Post by spuny on 2010-05-01
> **supermeip said:**
> how do you mount the drive

sorry I just edit my post mount means double click the partition name you don't have to mount through terminal

---

### Post by supermeip on 2010-05-01
is my c drive suposed to be under /media/ and what if they are both already there?


im going to try to reboot now

---

### Post by supermeip on 2010-05-01
didnt work nothing changed:(

---

### Post by spuny on 2010-05-01
Firstly click on Places > Computer
you will see a dialog with a partitions like in screenshot.png in my case the first partition is the c:\ one all I did was just double click on the partitions name, so you do the same double click on all of your partitions till you find the drive that contains your windows file this drive files will look like the one in screenshot-1.png after you find it extract the zip file i uploaded and copy paste in your windows drive, and it should be ok!

after you do that tell me what happened I will be around.

---

### Post by supermeip on 2010-05-01
thats what i did but it still dont work:( :( :(

---

### Post by supermeip on 2010-05-01
,[QUOTE=spuny][QUOTE=supermeip][QUOTE=spuny][QUOTE=supermeip][QUOTE=spuny][QUOTE=supermeip][QUOTE=spuny][QUOTE=supermeip]can  you pls help me it didn't work  [http://ubuntuforums.org/showthread.php?t=1468674&page=2](http://ubuntuforums.org/showthread.php?t=1468674&page=2)[/QUOTE]

did you copy files to c:\ drive or you couldn't find it? Also I see from  fdisk you post that you have two hard disks. Did you put windows on the  other hard or both on the same?[/QUOTE]

i only have one hard disk and is c:/ suposed to be under meia after i go  in it through compuer then up a dir[/QUOTE]

Check
 [http://ubuntuforums.org/showthread.php?p=9213474#post9213474](http://ubuntuforums.org/showthread.php?p=9213474#post9213474)  .. sorry I couldn't upload pics on private msg so I replied the  thread.[/QUOTE]
still nothing ![/QUOTE]


I'm searching for another solution, did you try last known good  configuration or restore mode ? to do so as I told you after you restart  your pc keep click on f8 then choose last known good configuration or  safe mode then on safe mode try restore mode.[/QUOTE]
f8 dosnt work[/QUOTE]

on your windows driver you will find file called boot.ini please open it  and paste it's contents for me maybe there's something wrong with this  file.[/QUOTE]

---

### Post by supermeip on 2010-05-01
vx[QUOTE=spuny][QUOTE=supermeip][boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home  Edition" /fastdetect /NoExecute=OptIn[/QUOTE]

Seems there's nothing wrong with windows loader. I don't know what the  problem, but I think you need windows XP disc or go to recovery mode and  recovery mode works if you didn't format your hard disk before or  repartitioned it. Try to get windows xp disc better.[/QUOTE]

---

### Post by supermeip on 2010-05-01
i dont have a menu.1st file in grub folder and im running grub 1.98 this is my grub.cfj```
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 59f0ecbe-701c-427b-9fb2-ff4d7c526e01
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 59f0ecbe-701c-427b-9fb2-ff4d7c526e01
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 59f0ecbe-701c-427b-9fb2-ff4d7c526e01
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=59f0ecbe-701c-427b-9fb2-ff4d7c526e01 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 59f0ecbe-701c-427b-9fb2-ff4d7c526e01
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=59f0ecbe-701c-427b-9fb2-ff4d7c526e01 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 59f0ecbe-701c-427b-9fb2-ff4d7c526e01
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 59f0ecbe-701c-427b-9fb2-ff4d7c526e01
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01cae7d4f00dce00
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 23224306-3c1d-48d3-8e0a-1a50ba540464
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=23224306-3c1d-48d3-8e0a-1a50ba540464 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 23224306-3c1d-48d3-8e0a-1a50ba540464
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=23224306-3c1d-48d3-8e0a-1a50ba540464 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

---

### Post by supermeip on 2010-05-01
l[QUOTE=spuny][QUOTE=supermeip]is ther any way i can get xp to run grub/  nogrub or some other boot loader , and also im running grub 1.98 or a  close # to that not grub2[/QUOTE]

Actually I don't know about running windows through another boot loader  ask on the forum, but probably you don't have a problem with your boot  loader it's something else.[/QUOTE]

---

### Post by vargon on 2010-05-01
Maybe the steps at this site would help:
[http://www.tinyempire.com/notes/ntldrismissing.htm](http://www.tinyempire.com/notes/ntldrismissing.htm)

---

