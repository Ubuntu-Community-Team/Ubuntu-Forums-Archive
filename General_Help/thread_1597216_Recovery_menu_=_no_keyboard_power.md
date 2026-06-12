---
title: "Recovery menu = no keyboard power"
date: 2010-10-15
forum: General Help
---

### Post by MyD0j0 on 2010-10-15
Well, this isn't a very good start...
 
I'm new...sorta...to linux and surely new to ubuntu. Anyway, about a week ago i installed unbuntu 10.04 lts onto a usb (included the loop file) and played around to evaluate options. I liked what I saw so I decided to do a hard install. Everything went well right up until reboot when my login screen freezes.
 
After light digging around in the forums i came accross [this post]("http://ubuntuforums.org/showthread.php?t=1589050&highlight=login+frozen") talking about chowning my home directory. So by pressing the power button and waiting 60 seconds for shutdown, I reboot holding shift to get into grub. Grub menu opens and I go to the recovery menu. 
 
And then power on my usb dies. And man o man that netroot looks like it may be the ticket. I have 2 usb keyboards that both stop working at the recovery menu. They both work fine if I boot up my usb installation, though.
 
The lack of feeling warm fuzzies aside, I'm curious how I go about chown my home directory so that my login doesn't freeze?
 
dell optiplex g280
1.5Gb RAM
80Gb SATA HD
Radeon 9200 vid w/ 256 mb RAM
 
Thanks and best regards,
 
MyD0j0

---

### Post by MyD0j0 on 2010-10-15
Ok, perhaps then there is a way to chown the home directory from the usb install i have?
 
thanks,
 
MyD0j0

---

### Post by drs305 on 2010-10-15
I was going to sugget going into BIOS to check your settings, but if the USB keyboard works normally during a regular boot that shouldn't be the problem.

Do you have a special kernel option for USB in your *GRUB_CMDLINE_LINUX_DEFAULT=* line in /etc/default/grub?

If so, put the same option on the *GRUB_CMDLINE_LINUX=* line.

Another thing you could try would be to add the following to the file as well, but I've never used these particular modules.

GRUB_PRELOAD_MODULES="usb usb_keyboard"

If you make any changes to this file, run "sudo update-grub" to update the Grub2 configuration file.

---

### Post by MyD0j0 on 2010-10-16
Well, drs305--I appreciate that info.  However, after going through the list of [Grub2 commands]("http://grub.enbug.org/CommandList"), there didn't appear to be any file editing capability so I then tried to follow this grub2 guide on [using cli to boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot") figuring I would boot to login prompt.  When I got to initrd /initrd.img, however, I kept getting told that there was no such file.
 
ls shows i have (hd0) (hd0,5) (hd0,1) (fd0)
in the cli boot guide i used these commands
[INDENT]set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro  (I also tried using sda0, 2 and 3)
initrd /initrd.img
[/INDENT]Either that section of the guide needs to be updated, or I'm heading down the wrong path in figuring out how to boot this thing to a login prompt so that I can login as root and modify these files (come to think of it, since this was the no fuss install--the LiveCD on my usb had an installer on the desktop--I don't recall ever being prompted to set a root password--just my own login info).
 
When I booted to my usb stick, i was able to check out the lines on the desktop install in /etc/default/grub that you mentioned and *GRUB_CMDLINE_LINUX_DEFAULT=*   was set to "quiet splash" or something to that effect and *GRUB_CMDLINE_LINUX=*   was just "".  I'm just curious how now how I can edit those files.
 
I have searched the forums for things like 'boot to command line' 'boot to login', etc but any post that ever used any 1 of those words in passing gets pulled up as a hit and sadly, there isn't enough time in the day to read through them all.  Can you tell me a little more about what I should be doing?
 
Thanks for the assistance!

---

### Post by drs305 on 2010-10-16
You can post the contents of RESULTS.txt from running the boot info script from here: [http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

It will tell us about what is happening with your boot.

To be honest, I don't really understand your situation. You talk about chowning your home directory, which should not be necessary unless you had previously messed up the permissions of your home folder. 

The mention of "waiting for your password" is an issue past what Grub has to do with the boot, as it has already passed control to the kernel by the time you are asked for any passwords.

The dead USB is something that might be solved by a BIOS or Grub kernel option...

As far as accessing your real files, you can boot the Live CD, mount your Ubuntu partition, and then edit the files. You can run commands that will effect your real installation by using *chroot*.

To edit your real files:
```
sudo mount /dev/sdXY /mnt
gksu gedit /mnt/etc/default/grub
```

You can use this method to edit files such as fstab, but editing the grub script files won't be enough because these files only update the grub configuration file after update-grub is run. To run it effectively, you would have to chroot into your installation.

---

### Post by drs305 on 2010-10-16
You can post the contents of RESULTS.txt from running the boot info script from here: [http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

It will tell us about what is happening with your boot.

To be honest, I don't really understand your situation. You talk about chowning your home directory, which should not be necessary unless you had previously messed up the permissions of your home folder. 

The mention of "waiting for your password" is an issue past what Grub has to do with the boot, as it has already passed control to the kernel by the time you are asked for any passwords.

The dead USB is something that might be solved by a BIOS or Grub kernel option...

As far as accessing your real files, you can boot the Live CD, mount your Ubuntu partition, and then edit the files. You can run commands that will effect your real installation by using *chroot*.

To edit your real files:
```
sudo mount /dev/sdXY /mnt
gksu gedit /mnt/etc/default/grub
```

You can use this method to edit files such as fstab, but editing the grub script files won't be enough because these files only update the grub configuration file after update-grub is run. You can't run "update-grub" from the LiveCD without chrooting first.

I have a guide on purging/reinstalling Grub 2, and it also would tell you how to chroot into your Linux partition if you wish:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by MyD0j0 on 2010-10-19
Sorry for taking so long to get back, but again, I do appreciate the help.  To clarify my problem:

First, the original problem was that during post-install reboot of Ubuntu, the system would get to the login window and stop.  The only action I could take was to press the power button and wait for the system to count down its 60 sec shutdown.  There was a forum post that seemed to match what my problem is and so I had been trying to do the same fix, which is to chown my home directory.  That forum post is linked in my original post.  Since then, I have also re-installed, but at the screen where I enter my login credentials, I unchecked the login at boot up option (or what ever it actually says) so that the system would just boot to the desktop.   The system will go to the desktop, but as soon as it is displayed, the system stops and no input (keyboard/mouse) seems to be accepted.   This is where I push the power button and wait 60 sec for shutdown to occur.

Second, the issue with grub2 was discovered while i was trying to use the rescue screen to to get to a command line login prompt to perform the file modification (without using a LiveCD/USB).  I don't believe that losing my usb power is a bios issue; I have only ever had an issue with usb in 2 cases: accessing Ubuntu's grub2 rescue graphical screen and while accessing gentoo's links browser while trying to install that system (which prevented me from going any further).  However, I had no problem using PING which is also graphical (a linux hard disk imaging LiveCD, which I used to image my Win XP installation prior to attempting to install Ubuntu/Gentoo), as well as other graphical systems (another example, I had created an avg rescue boot antivirus flash drive for working on my dad's system, which also uses a linux system) just a couple weeks ago.

All that said, it has been nearly 7 years since I have messed around with a *nix system in any capacity and I had forgotten about chroot.  I will try that later when I have a bit more time to mess around with things.  In the mean time, below is the contents of RESULTS.txt.  If you see anything in there that jumps out at you, please let me know.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

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

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   149,792,767   149,790,720  83 Linux
/dev/sda2         149,794,814   156,248,063     6,453,250   5 Extended
/dev/sda5         149,794,816   156,248,063     6,453,248  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.2 GB, 16231956480 bytes
256 heads, 54 sectors/track, 2293 cylinders, total 31703040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    31,703,039    31,703,008   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       aee869a8-eccb-e24c-9637-2dfa7bd81a86   ext2       casper-rw                     
/dev/sda1        f6e1844f-df39-45df-91a1-af437a279c9b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e80c6d14-f36d-4eab-b7cc-f19b326661be   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        445B-AC34                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set f6e1844f-df39-45df-91a1-af437a279c9b
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
search --no-floppy --fs-uuid --set f6e1844f-df39-45df-91a1-af437a279c9b
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
    search --no-floppy --fs-uuid --set f6e1844f-df39-45df-91a1-af437a279c9b
    linux    /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f6e1844f-df39-45df-91a1-af437a279c9b
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 ro single 
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f6e1844f-df39-45df-91a1-af437a279c9b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f6e1844f-df39-45df-91a1-af437a279c9b
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
UUID=e80c6d14-f36d-4eab-b7cc-f19b326661be none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  62.4GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
  62.4GB: boot/initrd.img-2.6.32-24-generic
  62.4GB: boot/vmlinuz-2.6.32-25-generic
  62.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  3b 8e 79 98 79 9a fc 5b  60 27 a5 a7 29 e6 c5 fb  |;.y.y..[`'..)...|
00000010  c9 cf 4f 53 7c 38 ec e1  f2 49 72 8f 84 9d 9c 38  |..OS|8...Ir....8|
00000020  49 f6 46 a0 d7 fb 24 79  f4 e8 df ea 2f 7b 52 e7  |I.F...$y..../{R.|
00000030  49 b5 ab 6c 19 fa 5f 7f  2a d5 3e d4 20 91 bf fd  |I..l.._.*.>. ...|
00000040  4b 3f 06 fd 8f 3d 45 ee  5b d0 0b fe 11 7e 9a 22  |K?...=E.[....~."|
00000050  b0 b3 d8 5d f8 be 05 ec  4b 6b 3c 9b b4 33 6d 95  |...]....Kk<..3m.|
00000060  b3 64 1b 05 7b f8 e4 34  ce 2f 30 fe c5 9f 90 f9  |.d..{..4./0.....|
00000070  41 e4 0f 6f 9e 25 29 11  cf 97 9c 25 76 1f f4 3e  |A..o.%)....%v..>|
00000080  e8 0c d9 90 d7 fa f7 9c  a1 60 3d d4 7b 4f 93 be  |.........`=.{O..|
00000090  2e e6 fb 8f d3 64 bf 09  7e ed cf 50 14 79 63 e4  |.....d..~..P.yc.|
000000a0  f9 73 e4 be 00 dc 77 86  f4 a7 31 9e 7c e8 ed 30  |.s....w...1.|..0|
000000b0  e8 3f 7b 9e dc 80 da e9  e7 c9 e6 03 1c 71 81 cc  |.?{..........q..|
000000c0  db a0 37 c3 05 62 eb d1  fe b3 0b 64 41 fe e6 3f  |..7..b.....dA..?|
000000d0  7a 01 71 18 74 72 2f 92  1e d0 78 e9 22 f9 af 00  |z.q.tr/...x."...|
000000e0  3f 7f 9e e2 d7 d0 6f ee  39 32 81 6e e4 c4 b9 94  |?.....o.92.n....|
000000f0  be d5 76 26 d8 a5 31 ef  0c 69 d6 c0 6e 1f f9 6b  |..v&..1..i..n..k|
00000100  7c 46 d0 15 df 42 7e d4  3b 4d 67 c8 73 1e f5 23  ||F...B~.;Mg.s..#|
00000110  ce 90 1f 76 2b 22 a7 29  84 fc 9c 1d 82 7c 80 91  |...v+".).....|..|
00000120  c2 8b 78 cf 82 f2 2d 17  49 03 dc 78 3d 42 c1 af  |..x...-.I..x=B..|
00000130  21 df f1 08 69 90 27 3b  97 7c 4a 02 f6 19 7a 05  |!...i.';.|J...z.|
00000140  b0 12 e2 9b ee 4b 0a c3  7e ec c7 bf a0 d0 fd 88  |.....K..~.......|
00000150  0b e3 3e c3 f7 31 b0 cf  78 e6 12 d9 1f 81 9d 77  |..>..1..x......w|
00000160  8b 90 01 79 a0 dd 7e 81  0c 9d 12 79 cf 05 8a 43  |...y..~....y...C|
00000170  bf 91 55 e7 29 d2 1a 71  6d c2 79 b2 42 8f d6 92  |..U.)..qm.y.B...|
00000180  8b 64 eb 8c 76 d1 4b e4  7a 12 78 e9 25 8a c2 9e  |.d..v.K.z.x.%...|
00000190  dd 0d 23 a9 72 f7 08 d8  71 eb 2f 28 9b 03 d6 fe  |..#.r...q./(....|
000001a0  94 8c d8 77 88 de 5f 50  60 1e e8 9d ff 92 d4 7a  |...w.._P`......z|
000001b0  95 8e 2a 4f 00 79 65 64  e1 97 a4 fb 0c f2 00 fe  |..*O.yed........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 62 00 00 00  |...........xb...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by drs305 on 2010-10-19
From your last post, I gather that Grub is working and you are able to boot. You have made some changes to your system since your original post so you might want to restate what current problem(s) continue to plague you.

The file results look fairly normal, other than it's not using UUIDs to identity the partitions. That's usually not an issue. If Grub isn't working in cases like this I usually recommend purging and reinstalling just to clean everything out and reset it to the default settings.

As far as not having some capabilities in the recovery mode - the kernel options in the GRUB_CMDLINE_LINUX_DEFAULT don't get added when the recovery mode is run. If you need a specific capability in the recovery mode, add the option in GRUB_CMDLINE_LINUX of /etc/default/grub. Presently you have no extra kernel options in either setting (other than the default *quiet splash*.

---

### Post by MyD0j0 on 2010-10-19
The *only* change I made was to re-install ;) so as to turn off the login prompt.  The end result is the same as when being prompted at the login window, once the system gets either to the login window or the desktop, the system freezes.  All I can do at that point is shut it down using the power button.

On another note, from the liveusb, I don't seem to be able to 'sudo chown -R myd0j0 /home/myd0j0' as there is no such user (that is the user on the desktop system, not the LiveUSB) and when I try to chroot i get 'operation not permitted'.

---

