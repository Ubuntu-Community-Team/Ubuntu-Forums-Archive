---
title: "I cannot boot my computer, and am completely clueless."
date: 2011-02-21
forum: General Help
---

### Post by Jepcats on 2011-02-21
**Please excuse the wall of text, I just wanted to let you know everything that has happened. Sorry if I provide you with unnecessary information. I really don't know much about this kind of thing.**

I'll give you a quick run down on what my problem is, what I did before-hand and what I've tried to do (and failed miserably and created further problems) to try and fix it. If you know of a forum where I might get better help, please direct me to it, but I thought you guys would be the best to ask. I am not the most technically aware person, but do know a bit.

Problem: I cannot boot my computer. I can get past the first screen that comes up where it says "SAMSUNG" where I can take it into setup, it then goes on to the next screen which says "Boot from AHCI:" or something. I can't quite remember. and that's where it just restarts and goes back to the Samsung screen and repeats this loop.

What I did: I created a dual boot whatever where I wanted to run Ubuntu and Windows 'alongside' each other. I used Ubuntu for a few days before I needed to do something in Windows. I rebooted up my computer, chose Windows Vista and it took me into Samsung Recovery. I cancelled Samsung Recovery and rebooted again. That's when it did this looping boot thing. I put the Ubuntu CD back in again and reinstalled Ubuntu. 
By this time I'm guessing I have two different installations of Ubuntu on my external hard drive. I backed up all the stuff I needed on my C drive to my (500GB) external hard drive, which can no longer take any more files. I tried booting WIndows Vista again to see if it was just a glitch, and it happened again. I then reinstalled Ubuntu AGAIN to my external hard drive, thinking I was so clever and could probably get it fixed on my own, which I couldn't. Blah blah more idiotic failings followed, and I even tried to install on my memory stick even though I had NO idea what I was trying to do. Yes, I know. I could have just clicked "Try Ubuntu" and it would have been easier, like I have now. That's how I'm posting this.
ANOTHER stupid thing I tried was to actually use this Samsung Recovery thing. I tried a "Basic Recovery" where it kept my files and that didn't work, so then I tried a "Complete Recovery" which basically deleted the stuff off my C drive and that didn't work either, but it's okay 'cause most of my stuff is on my external hard drive.
I then fiddled around in the Setup thing on the Samsung screen, but nothing worked. I just changed settings that sounded like they might change the way my machine booted, but changed them all back when I was done. 
Basically, I've grasped at anything that I can actually do and done it. Seeing as I can't get past anything but that Samsung setup screen or boot from this CD; I can't do much.

I'd be eternally grateful if any of you could help me with my problem, if any of you actually managed to read through this stress-filled post filled with unnecessary information and ramblings.
Also, it'd be nice if someone could tell me how to delete the several Ubuntu partitions I've created, too.
Yeah, okay. Stop shaking your heads at my idiocy. I know I'm uneducated on this sort of thing.

Thank you very, very much in advance.

---

### Post by coldraven on 2011-02-21
Boot with the live CD, select "Try Ubuntu".
Run Gparted         System>Admin>Gparted Partition Editor
Then presuming you have backed up your stuff!!
Make sure you **select the** **correct drive** with the drop down menu in the top right corner!
Delete any partitions that are formatted EXT4
If they are adjacent, create a new one in the available space.
You could then format the new partition to NTFS so that windows will see it.
Or try again to install Ubuntu.
Windows still won't boot unless you boot with a Windows recovery disc and use fixmbr.
None of this will apply if you used Wubi, of which I know nothing.

---

### Post by Jepcats on 2011-02-21
Thank you very much for your reply. I've deleted all the paritions EXT4, but I don't understand any of this:

[I]If they are adjacent, create a new one in the available space.
You could then format the new partition to NTFS so that windows will see it.
Or try again to install Ubuntu.[/I]

Sorry :( Like I said, my knowledge is limited.

Edit: I decided to take a screenshot so you can see and I don't make a mistake, as I'm very scared of just completely messing up.
[IMG]http://img833.imageshack.us/img833/2018/screenshotjln.jpg[/IMG]

[I]Windows still won't boot unless you boot with a Windows recovery disc and use fixmbr.
None of this will apply if you used Wubi, of which I know nothing.

[/I]I don't think I use Wubi... I borrowed my friend's Ubuntu installation CD to install it, so I'm unsure. How would I find out?
Also, do I need to download the Windows recovery disc and burn it onto a CD/DVD or should I already have one somewhere?

---

### Post by Quackers on 2011-02-21
The changes in gparted are shown as pending. Did you click on the green arrow to apply the changes? If not, don't do it!
From the live cd desktop please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Installing and re-installing something is not usually the answer. It is better to ask about what you are doing and why something is not working. You now have partitions all over the place and you don't know what's in what.
Did you make a set of recovery dvd's for Windows? Did you make a repair cd for Windows? These things would have been more productive, as you may need both.

---

### Post by Jepcats on 2011-02-21
I didn't click the green tick and have undone the deletions of the EXT4 partitions.[I]

"Did you make a set of recovery dvd's for Windows? Did you make a repair  cd for Windows? These things would have been more productive, as you may  need both."

[/I]No, I did not do this. I don't know how I would have gone about doing that; or will do that, if you want me to, as I can use another computer to access Windows XP and I can get my hands on some CDs/DVDs to write to.

The RESULTS.txt is this:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden HPFS/NTFS
/dev/sda2    *     27,265,024   325,242,879   297,977,856   7 HPFS/NTFS
/dev/sda3         325,242,880   625,139,711   299,896,832   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   641,878,852   641,878,790   7 HPFS/NTFS
/dev/sdc2         641,880,062   976,771,071   334,891,010   5 Extended
/dev/sdc5         754,022,400   860,827,647   106,805,248  83 Linux
/dev/sdc6         967,634,944   976,771,071     9,136,128  82 Linux swap / Solaris
/dev/sdc7         641,880,064   749,348,863   107,468,800  83 Linux
/dev/sdc8         749,350,912   754,010,111     4,659,200  82 Linux swap / Solaris
/dev/sdc9         860,829,696   963,170,303   102,340,608  83 Linux
/dev/sdc10        963,172,352   967,626,751     4,454,400  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AC5C11485C110F28                       ntfs       RECOVERY                      
/dev/sda2        7608133F0812FE35                       ntfs                                     
/dev/sda3        F6789992789951EB                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc10       6a036ab1-40dd-4d3b-809b-626ab0c07bef   swap                                     
/dev/sdc1        CE40A0FA40A0EA83                       ntfs       Expansion Drive               
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        b1631105-c890-4ed3-83d2-bb4b72b8d15b   ext4                                     
/dev/sdc6        5516b6e3-d1d0-4b44-b41c-2c939c983f09   swap                                     
/dev/sdc7        453a3dec-eebf-48a2-8eb8-82b6bd13e682   ext4                                     
/dev/sdc8        b0dd9686-3b26-46c3-b306-79c3caa083ff   swap                                     
/dev/sdc9        cefe9b8d-574c-49f4-9d22-2d314678d9bd   ext4                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/F6789992789951EB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/7608133F0812FE35  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ac5c11485c110f28
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 7608133f0812fe35
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

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=5516b6e3-d1d0-4b44-b41c-2c939c983f09 none            swap    sw              0       0

=================== sdc5: Location of files loaded by Grub: ===================


 427.0GB: boot/grub/core.img
 386.6GB: boot/grub/grub.cfg
 387.3GB: boot/initrd.img-2.6.35-22-generic
 387.4GB: boot/initrd.img-2.6.35-25-generic
 427.0GB: boot/vmlinuz-2.6.35-22-generic
 427.0GB: boot/vmlinuz-2.6.35-25-generic
 387.4GB: initrd.img
 387.3GB: initrd.img.old
 427.0GB: vmlinuz
 427.0GB: vmlinuz.old

=========================== sdc7/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set 453a3dec-eebf-48a2-8eb8-82b6bd13e682
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set 453a3dec-eebf-48a2-8eb8-82b6bd13e682
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 453a3dec-eebf-48a2-8eb8-82b6bd13e682
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=453a3dec-eebf-48a2-8eb8-82b6bd13e682 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 453a3dec-eebf-48a2-8eb8-82b6bd13e682
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=453a3dec-eebf-48a2-8eb8-82b6bd13e682 ro single 
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
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 453a3dec-eebf-48a2-8eb8-82b6bd13e682
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 453a3dec-eebf-48a2-8eb8-82b6bd13e682
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ac5c11485c110f28
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 7608133f0812fe35
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sdc7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=453a3dec-eebf-48a2-8eb8-82b6bd13e682 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=b0dd9686-3b26-46c3-b306-79c3caa083ff none            swap    sw              0       0

=================== sdc7: Location of files loaded by Grub: ===================


 333.0GB: boot/grub/core.img
 358.8GB: boot/grub/grub.cfg
 358.9GB: boot/initrd.img-2.6.35-22-generic
 328.9GB: boot/vmlinuz-2.6.35-22-generic
 358.9GB: initrd.img
 328.9GB: vmlinuz

=========================== sdc9/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos9)'
search --no-floppy --fs-uuid --set cefe9b8d-574c-49f4-9d22-2d314678d9bd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos9)'
search --no-floppy --fs-uuid --set cefe9b8d-574c-49f4-9d22-2d314678d9bd
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
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set cefe9b8d-574c-49f4-9d22-2d314678d9bd
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=cefe9b8d-574c-49f4-9d22-2d314678d9bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set cefe9b8d-574c-49f4-9d22-2d314678d9bd
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=cefe9b8d-574c-49f4-9d22-2d314678d9bd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set cefe9b8d-574c-49f4-9d22-2d314678d9bd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cefe9b8d-574c-49f4-9d22-2d314678d9bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set cefe9b8d-574c-49f4-9d22-2d314678d9bd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cefe9b8d-574c-49f4-9d22-2d314678d9bd ro single 
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
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set cefe9b8d-574c-49f4-9d22-2d314678d9bd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set cefe9b8d-574c-49f4-9d22-2d314678d9bd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ac5c11485c110f28
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 7608133f0812fe35
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set b1631105-c890-4ed3-83d2-bb4b72b8d15b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=b1631105-c890-4ed3-83d2-bb4b72b8d15b ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 453a3dec-eebf-48a2-8eb8-82b6bd13e682
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=453a3dec-eebf-48a2-8eb8-82b6bd13e682 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set 453a3dec-eebf-48a2-8eb8-82b6bd13e682
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=453a3dec-eebf-48a2-8eb8-82b6bd13e682 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sdc9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb9 during installation
UUID=cefe9b8d-574c-49f4-9d22-2d314678d9bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb10 during installation
UUID=6a036ab1-40dd-4d3b-809b-626ab0c07bef none            swap    sw              0       0

=================== sdc9: Location of files loaded by Grub: ===================


 443.0GB: boot/grub/core.img
 490.3GB: boot/grub/grub.cfg
 441.7GB: boot/initrd.img-2.6.35-22-generic
 441.8GB: boot/initrd.img-2.6.35-25-generic
 443.0GB: boot/vmlinuz-2.6.35-22-generic
 443.0GB: boot/vmlinuz-2.6.35-25-generic
 441.8GB: initrd.img
 441.7GB: initrd.img.old
 443.0GB: vmlinuz
 443.0GB: vmlinuz.old
```

---

### Post by Quackers on 2011-02-21
Ok thanks. You have some work to do :-)
Your system appears to be fixable, so don't worry.
Firstly download a Windows 7 (if that's what you're using) repair disc iso file and burn the image to a cd. It's not too big a file so shouldn't take too long.
Start that going and I'll get back to you in a minute.

Option 2 in this link may help
[http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)

---

### Post by Quackers on 2011-02-21
While that's downloading go into gparted again (from the live cd desktop) and, making sure you have /dev/sdc chosen, right-click on each of the swap partitions in turn and select "swapoff".
When they are turned off, right-click on sdc8 and select delete, then on sdc10 and select delete. Click on green arrow to apply the change. This will delete 2 of your swap partitions, leaving just one. As there is a discrepancy in the numbering check that they are the last 2 swap partitions on the disc.
When that's run, right-click on sdc9 and select delete, then on sdc7 and select delete. These are your last 2 ext4 partitions, check that is correct. If so, click on the green tick to apply.
You should now be left with only sdc1, sdc2,sdc5 (ext4) and sdc6 (swap) on that disc. Check that.
Please enclose screenshot of that for confirmation, thanks.

---

### Post by Jepcats on 2011-02-21
Sorry to be a pain, but I deleted sdc 10 and 8 before I read what you'd said about checking that they are the last ones on the disc, and I definitely deleted sdc 10 and 8.
But I'm left with 1, 2, 5, 6, 7 and 8. 5, 7 and 8 are all ext4. Just checking if I've made a mistake because you've said delete sdc 9 but it isn't there. Did it delete when I deleted one of the others? Do you want a screenshot? Again, sorry. Oh, and I didn't have my USB plugged in when I ran that terminal command... Is that an issue? There's one installation of Ubuntu on there too. All I've done is deleted sdc8 and 10. I just don't feel as if I've done this right.

---

### Post by Quackers on 2011-02-21
Hmm it was a bit strange because gparted didn't have the same partition info as the boot script output did.
Please post a screenshot of gparted screen for /dev/sdc, thanks.

Also can you tell me which hard drive is set to boot first in your bios?

---

### Post by Jepcats on 2011-02-21
**EXTERNAL HARD DRIVE PARTITIONS:** (after deletion of sdc8 and 10 (supposedly))

[IMG]http://img267.imageshack.us/img267/8813/screenshotmw.jpg[/IMG]

[B]USB PARTITIONS:
[IMG]http://img824.imageshack.us/img824/5334/screenshot2kj.jpg[/IMG]



[/B]Oh, and to check which runs first in my BIOS I have to restart and go into that Samsung setup screen don't I? That would mean I'd lose the files I've got on my desktop from this live CD wouldn't it? Anyway, if I remember correctly from rummaging around in the BIOS before it boots first from the main thing but with "CD" on the end, then secondly the main thing without anything, I think. That probably doesn't tell you anything and I'm not entirely sure, but I'm scared to restart.

---

### Post by Quackers on 2011-02-21
Ok I understand.
Ignoring sdd for now, (which can be unplugged when we've finished, and re-formatted at any time) go to sdc.
Assuming that sdc6 (swap) is still in the swapoff state, delete partitions sdc7 and sdc8. Apply the change.
That should leave the disc with sdc1 and sdc2 (which includes sdc5 and sdc6).

Ok, now you have to boot from the Windows repair cd you made. But first you must make sure that the Windows drive (320GB I believe) is the second boot device in your bios (after cd drive).
To enter bios you may have a one time only boot change key. It is often the F12 key (but can be something else) which you need to tap during the initial boot process. Or, alternatively there will be a key to tap during boot to actually enter your bios settings and make permanent changes. You will need to know what that key is for your machine.
When in your bios, you need to make sure that the Windows drive is second boot device (after cd drive) and that the usb drive (500GB I believe) is third boot device.
Having done that, boot from the Windows repair disc and press R for the repair console, then choose the Command Prompt option.
When that window opens up type in ```
bootrec.exe /fixmbr
```
Note the space between exe and /fixmbr.
Hit enter and if it runs without errors, take the cd out of the drive and reboot. Windows should now boot directly.
We can fix Ubuntu after.

---

### Post by Jepcats on 2011-02-21
It didn't work.

In the BIOS the boot order was:

AHCI-CD
AHCI-HDD
USB HDD

Just like you said. It was making an unpleasant noise when I was choosing the boot order, then when I exited and saved the changes it was making the same noise (which was hopeful) on the boot from AHCI-CD screen, it stayed there for longer than usual then it went blank, then all of  asudden goes back to that same Samsung initial screen before it tries to start booting, then went onto the AHCI thing again but this time only stayed there for a second at most, then repeated this process.
Any ideas?

---

### Post by Quackers on 2011-02-21
Unpleasant noise? Don't know what that is.
What happened when you ran bootrec.exe /fixmbr?

---

### Post by Jepcats on 2011-02-21
Just mentioned the noise because it was consistent, spaced and was kind of like a loud whirring. It's probably normal though?

I didn't actually get a chance to because it didn't actually boot up at all. I got past the initial Samsung screen like before, then when it tried to boot it didn't and just restarted. Is there something else I should have done?

---

### Post by Quackers on 2011-02-21
Did you put the Windows repair disc in the drive before you rebooted?

---

### Post by Jepcats on 2011-02-21
Yes, I put it in as I pressed the power button. I couldn't put it in before that because it's not a disc tray and needs to be on. I've tried again once after too and it did the same as what I described in my last post. 
Can I also say that I appreciate the help and if this were in person you wouldn't be able to speak for all my thanks, even if I don't manage to get this working.

---

### Post by Quackers on 2011-02-21
No problem.
It makes it difficult to try something then, when that fails, you have to boot from a live cd again. I appreciate that.
How did you burn the Windows repair iso file to the disc? What software did you use?

---

### Post by Jepcats on 2011-02-21
I used another computer using the software ImgBurn to burn the Vista repair disc.

---

### Post by Quackers on 2011-02-21
If you selected burn image rather than just burning the files that should be ok. Imgburn has worked fine for me in the past.
Somewhere on the cd drive there will be a button or a pinhole to push a pin in to open the drawer. Turn off the computer, open the drive and put in the Windows disc and close the drive. Then press the power button to boot the machine.
Watch the screen and at some time it should ask you to press any key to boot from cd. Press any key then it will ask you to press R for the recovery console. Try that.
If you can't get the pc to boot from the cd we're doomed :-)

---

### Post by Jepcats on 2011-02-21
I had to press F12 on the Samsung screen to go into a pre-executuion environment, out of pure luck. It asked me to press a key to boot from the CD like you said. 
I've chosen my language and keyboard layout and I'm now on a screen that presents me with 3 options:

Install now (the main big button)
What to know before installing Windows
Repair your computer

Which do I click? It's probably Repair your computer but I'm unsure as what you said didn't seem to include any of this.

---

### Post by Quackers on 2011-02-21
You can try "repair your computer" then see if there is a command prompt option in the advanced section and type ```
bootrec.exe /fixmbr
```  If no advanced section try the automatic startup rerpair.

---

### Post by Jepcats on 2011-02-21
I typed the command and it said "The operation completed successfully."
What do I do now? Oh and can I eject from this prompt because my laptop doesn't actually have a tray, it's like the PS3, you just slide the disc in. If I don't have to eject it then never mind. I'll just restart.

---

### Post by Jepcats on 2011-02-21
<snip-double posted>

---

### Post by Quackers on 2011-02-21
Ok, Now reboot and hopefully Windows should boot up.
Eject the cd by whatever means you can. If not just let the system boot to Windows and eject the cd later.

---

### Post by Jepcats on 2011-02-21
Sorry for the slow reply, everything worked and I've managed to boot up Windows fine :D
When I chose Complete Restore though before I came for advice, it restored to an earlier time when my login password was different. This is very embarrassing to admit after all this, and I don't know whether to laugh or cry. I'll get back to you when I remember it though, so bare with me. I've got a password hint to help jog my memory.

---

### Post by Quackers on 2011-02-21
Ok, no problem. 
Then we can fix Ubuntu :-)

---

### Post by Jepcats on 2011-02-22
Hello again. Couldn't remember my password and had to use software to get it, but never mind. How do I go about fixing Ubuntu then? :)

---

### Post by Quackers on 2011-02-22
Ok I will write a couple of commands for you.
These commands will change depending on 2 variables.
The first is what drive designations do your disks have now? In other words, are your 2 hard drives still sda and sdc (check in gparted) as they can change if you plug things in and out again.
Secondly, can you make a permanent change to your bios, so that sdc (your 500GB drive) is second boot device - ie after cd drive, but before the internal HDD? (Not just on a one time only basis, but all the time).

---

### Post by Quackers on 2011-02-22
Did you fall asleep on me?  :-)

---

### Post by Jepcats on 2011-02-22
I'm so sorry about that, I had a call from someone and I had to go see them. I'm back now though!

I've made the permanent change to the BIOS. 
My internal HDD is sda, but my external HDD has decided to be sdb.

---

### Post by Quackers on 2011-02-22
Ok, are you booted into the live cd now?

---

### Post by Jepcats on 2011-02-22
I am indeed.

---

### Post by Quackers on 2011-02-22
Hokey cokey.
Please open a terminal and copy/paste these commands into it, one line at a time and pressing enter after each line
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

This is assuming that your Ubuntu root partition is sdb5 - check in gparted for the only ext4 partition left. I think it is.

It should report that it ran without reporting any errors. If it does reboot, take the live cd out and hopefully Ubuntu will boot right up.
If it does, open a terminal and run 
```
sudo update-grub
```
enter your password and watch as grub.cfg is configured. It should pick up the Windows Loader. 
If it does, reboot again, and your new grub menu should include entries for Ubuntu and Windows. Try booting each and make sure they both work.
If that goes ok, you're done :-)

---

### Post by Jepcats on 2011-02-22
It was all going so well until I tried to boot Windows *sigh* It took me to Samsung Recovery Solution III again, like it did last time I tried to boot in Windows. Does it think I'm clicking the recovery option or what?
Although, last time that happened when I rebooted afterwards it did that looping boot, this time it has let me boot into Linux again.  

Can I also just check that this is ok:
[IMG]http://img267.imageshack.us/img267/8151/screenshotku.jpg[/IMG]

Is there supposed to be two different Linux entries?

---

### Post by Quackers on 2011-02-22
Are you selecting the Vista Loader on /dev/sda1?
Sadly, sometimes with Vista, grub detects the Windows partitions and mis-labels them.  As your Windows operating system is on /dev/sda2, that's the one you should be selecting to boot Windows :wink:

---

### Post by Jepcats on 2011-02-22
So I should choose the Windows Vista Recovery option to boot Windows?... Just making sure.

If this works, you're a God.

---

### Post by Quackers on 2011-02-22
Yes. And I'm not, I've just been there myself :-)

---

### Post by Jepcats on 2011-02-22
That's that then. All done.  Thank you very, very much for the clear information and for taking it slowly with me, it's very much appreciated.

---

### Post by Quackers on 2011-02-22
WooHoo :-) that's good news!
You're very welcome!

When something doesn't work how it should in future, don't pile layer upon layer of confusion on top of things :-)  Find out what's wrong, or if you can't do that, ask on here. There are oodles of people here with vast experience. One of them is likely to have seen your problem before.

Please mark the thread as solved, using the Thread Tools near the top of the page.

---

