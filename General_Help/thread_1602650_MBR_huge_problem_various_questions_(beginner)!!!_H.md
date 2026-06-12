---
title: "MBR huge problem various questions (beginner)!!! HELP"
date: 2010-10-21
forum: General Help
---

### Post by awd01 on 2010-10-21
[SIZE=2]Hello guys i am using ubuntu for about one month and everything was running almost smoothly until I did the following.

I wanted to install also windows 7 just to play some games.. i cant escape from bad habits. So, i made another partition and I said now i am ready to install the stupid windows. I insert my CD but an error has occurred.. when i had to select the partition that i want to install windows it said that it cant be installed because the partition (every partition) was unrecognizable. Furthermore, I started searching the first thing i thought is the file system.. it was in ext2 i convert it to NTFS but nothing changed. So after many hours i read something about the Master boot record (i dont know yet what is this thing) so i found the command and i installed it in the partition (i put sd3 not sd1(the ubuntu partition)) that i want to install windows. After that i receive an error that says 

[SIZE=4][COLOR=Red]"" Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions.
Anywhere else Tab lists the possible completions of a device/filename.""[/COLOR][/SIZE][/SIZE] 
[SIZE=2]I am writing these running the ubuntu cd and i can mount my HD. 
I learn to search first and ask then but this time i think it was better to ask first.[/SIZE]

---

### Post by UnterUn on 2010-10-21
Reinstall Ubuntu to original state (from the disc) and install Wine to run windows programs *within* Ubuntu.
```
sudo apt-get install wine
```

---

### Post by awd01 on 2010-10-21
> **UnterUn said:**
> Reinstall Ubuntu to original state (from the disc) and install Wine to run windows programs *within* Ubuntu.
```
sudo apt-get install wine
```

m8 thank you for your help but i know all these things and this solution is not in my options. thank you for your time

---

### Post by Quackers on 2010-10-21
How did you make another partition for Windows? Was it with Gparted from your booted up Ubuntu system?

---

### Post by awd01 on 2010-10-21
> **Quackers said:**
> How did you make another partition for Windows? Was it with Gparted from your booted up Ubuntu system?

i run gparted from a cd and i made another1 partition. Can i just delete the MBR? I

---

### Post by 101011010010 on 2010-10-21
Hello, have you tried letting Windows create the partition ? Try deleting the partition, boot from the Windows disk and it should find the free space. You'll have to update grub after the install.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I hope this helps.

---

### Post by Quackers on 2010-10-21
> **awd01 said:**
> i run gparted from a cd and i made another1 partition. Can i just delete the MBR? I

No, the normal way to deal with mbr problems is to over-write it.
Did you resize the Ubuntu partition to make space for your new partition or was there space already?

---

### Post by awd01 on 2010-10-21
> **Quackers said:**
> No, the normal way to deal with mbr problems is to over-write it.
Did you resize the Ubuntu partition to make space for your new partition or was there space already?

i resized the partition but ubuntu were running fine. The problem occured when i installed MBR. Any ideas?

---

### Post by Quackers on 2010-10-21
Ok. I'm not absolutely sure what you installed to the mbr, if anything. If you were trying to re-install grub that should be to sda (if you only have one hard drive) not sd3.
It may help if you can go to the site below and download the boot info script to your desktop. Then run it with the command posted on that site. When it's run it will create a Results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your nest post. (For code tags click on New Reply then on the # symbol in the toolbar)

---

### Post by awd01 on 2010-10-21
[SIZE=2]i visit this link ```
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
``` when i run the commands for 9.10 and beyond the system** didnt** start again after the restart.
[/SIZE]

---

### Post by awd01 on 2010-10-21
> **Quackers said:**
> Ok. I'm not absolutely sure what you installed to the mbr, if anything. If you were trying to re-install grub that should be to sda (if you only have one hard drive) not sd3.
It may help if you can go to the site below and download the boot info script to your desktop. Then run it with the command posted on that site. When it's run it will create a Results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your nest post. (For code tags click on New Reply then on the # symbol in the toolbar) 

which site m8 :)

---

### Post by Quackers on 2010-10-21
I'm really sorry. I keep doing that :-) It's my age.
Here it is
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by awd01 on 2010-10-21
> **Quackers said:**
> I'm really sorry. I keep doing that :-) It's my age.
Here it is
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

haha no problem!! Thank you very much for your time my friend! I'll run your script and i'll pray!
I'll answer when i try this! If i fix it.. finally which one is the right way to install windows 7 in another partition?

---

### Post by Quackers on 2010-10-21
I would get Ubuntu booting normally first.
Once Ubuntu is up and running you would run the Windows cd and tell it where to install Windows (anywhere but on the Ubuntu partition). However I'm not entirely sure your partition table is in order. The bot script may give a clue.

---

### Post by awd01 on 2010-10-21
> **Quackers said:**
> I would get Ubuntu booting normally first.
Once Ubuntu is up and running you would run the Windows cd and tell it where to install Windows (anywhere but on the Ubuntu partition). However I'm not entirely sure your partition table is in order. The bot script may give a clue.

I run the script! the results are the following:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,049,677,823 1,049,675,776  83 Linux
/dev/sda2       1,232,130,046 1,250,263,039    18,132,994   5 Extended
/dev/sda5       1,232,130,048 1,250,263,039    18,132,992  82 Linux swap / Solaris
/dev/sda3       1,049,688,064 1,232,115,711   182,427,648  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     7,843,839     7,835,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1bf88fb0-f0d0-495b-8251-25db15ff7a5c   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        15A27EAC13002934                       ntfs       Partition 3                   
/dev/sda5        bfaf2a43-8130-486d-a717-d08661b6723b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0E67-B4DA                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/1bf88fb0-f0d0-495b-8251-25db15ff7a5c ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1bf88fb0-f0d0-495b-8251-25db15ff7a5c
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1bf88fb0-f0d0-495b-8251-25db15ff7a5c
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1bf88fb0-f0d0-495b-8251-25db15ff7a5c
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=1bf88fb0-f0d0-495b-8251-25db15ff7a5c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1bf88fb0-f0d0-495b-8251-25db15ff7a5c
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=1bf88fb0-f0d0-495b-8251-25db15ff7a5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1bf88fb0-f0d0-495b-8251-25db15ff7a5c
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1bf88fb0-f0d0-495b-8251-25db15ff7a5c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1bf88fb0-f0d0-495b-8251-25db15ff7a5c
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1bf88fb0-f0d0-495b-8251-25db15ff7a5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1bf88fb0-f0d0-495b-8251-25db15ff7a5c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1bf88fb0-f0d0-495b-8251-25db15ff7a5c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bfaf2a43-8130-486d-a717-d08661b6723b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 446.8GB: boot/grub/core.img
  30.9GB: boot/grub/grub.cfg
 446.9GB: boot/initrd.img-2.6.32-24-generic
 447.0GB: boot/initrd.img-2.6.32-25-generic
 446.8GB: boot/vmlinuz-2.6.32-24-generic
 446.9GB: boot/vmlinuz-2.6.32-25-generic
 447.0GB: initrd.img
 446.9GB: initrd.img.old
 446.9GB: vmlinuz
 446.8GB: vmlinuz.old

=================== sda3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img




```

---

### Post by Quackers on 2010-10-21
You need to re-install grub properly. It is looking for grub files in sda3. It should be looking in sda1.

If you are booted into the Ubuntu Live CD
open a terminal and type
sudo mount /dev/sda1 /mnt
enter password then
sudo grub-install --root-directory=/mnt /dev/sda

Then try rebooting your system without the live cd in the drive. If it works Ubuntu should boot up again.
If it doesn't work we may have to purge grub then re-install it, so boot back into the Live cd again please.

---

### Post by awd01 on 2010-10-22
My friend, I put your commands and there is an answer about install_device not specified 
What do we do now? :):

```
 To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/dev/sda
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.
ubuntu@ubuntu:~$ ^C
 
```

---

### Post by Quackers on 2010-10-22
You were a space missing in the second command
sudo grub-install --root-directory=/mnt /dev/sda
after the last /mnt and before the /dev/sda at the end

---

### Post by awd01 on 2010-10-22
> **Quackers said:**
> You were a space missing in the second command
sudo grub-install --root-directory=/mnt /dev/sda
after the last /mnt and before the /dev/sda at the end



[FONT=Courier New][SIZE=4][COLOR=DarkOrange]Installation finished. No error reported.[/COLOR][/SIZE][/FONT]

I like you because you answer instantly  even after 8 hours if I post smth again!!!
I restart now
[I][B][FONT=Impact]
[/FONT][FONT=Impact][SIZE=3][COLOR=Blue]THANK YOU VERY MUCH M8[/COLOR][/SIZE][/FONT][/B][/I][FONT=Lucida Sans Unicode]
[/FONT]

---

### Post by Quackers on 2010-10-22
You're very welcome :-)
Maybe you've just been lucky that sometimes I don't sleep :-)
I will be sleeping very soon!

---

