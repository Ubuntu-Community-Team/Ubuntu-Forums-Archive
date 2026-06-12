---
title: "Ubuntu 10.04 suddenly went into busybox mode, saying it can't mount some drives"
date: 2011-11-25
forum: General Help
---

### Post by skytreader on 2011-11-25
[First let me apologize: I was in a pretty bad mood when this started happening so I didn't take down notes of what was happening. Clear mistake. Here's to hoping some guru out there can fill in some of my blanks.]

I'm on a Gateway laptop that's around 3-4 years old, give or take, which frequently overheats. I sure panicked when it first overheated and then auto shutdown on me but as there doesn't seem to be any damage when that happens, I passed it off as something that should be avoided but not dangerous (at least, not very).

A bit more history:
My first Ubuntu installation was 9.10, about 1.5 years ago (March/April 2010). I didn't have any life-threatening issues while using it. I upgraded to my current version, 10.04 around a year ago (Oct. 2010) and it is only in 10.04 that I had overheating issues. I'm not blaming Lynx for the overheats---the first overheat cases were largely due to programming errors on my part---but lately, my laptop overheats even while doing the most mundane tasks (randomly, not all the time), as I'll relate next.

So this morning I was watching some YouTube videos when my laptop overheated and then auto shut down. So, I took a break from my computer, ate some lunch, and then returned afterwards to start working again.

Then, when I booted I found myself greeted by the busybox terminal, saying something about some drives that can't be booted. Something like from root/x though it listed 2 others, one from root, one not (here's when I didn't take note, sorry). Then, here's a list of what I did:

(1) I tried running "mount root/x", root/x being one of those drives it indicated. Fail. I typed "exit", it printed some more cryptic errors about me trying to "kill init" or something. I shut down manually from the switch.

(2) Tried booting my Vista partition (Note: GRUB loads fine). Works fine. Restart then Ubuntu again. Busybox greets me once more so I type exit and shut down as before.

(3) I booted from an 11.04 Live CD. Works fine. I navigated to my Ubuntu partition to check my files...all fine.

(4) I tried connecting to the internet to report whats happening (here to the forums, yes). I click on the network icon at the taskbar, click the name of our home network and then suddenly, I get logged out. I'm thinking if it was a mouse mistake on me but I'm unsure...

(5) So, 11.04 is now asking me for a username and a password which I obviously don't have for it. Defeated, I shut down.

(6) I run 10.04 again, and this time, busybox doesn't appear. It starts a disk check though, noting me of some errors. I say fix and then it says the "/tmp is not ready". I chose to continue anyway.

(7) System restarts, no busybox but Ubuntu does a disk check again. Runs fine this time and I finally get to log-in (my current session as I type this).

(8 ) I check around my stuff...everything seems fine. I check on my disks and it reports nothing noteworthy (save for one bad sector but it's been there since summer and I have reasons to believe that this is Vista's fault).

Some more stuff:
/tmp# ls -all
```
total 80
drwxrwxrwt 17 root root 12288 2011-11-25 16:02 .
drwxr-xr-x 21 root root  4096 2011-11-12 23:57 ..
drwx------  2 skrd skrd  4096 2011-11-25 15:33 .com.google.Chrome.kYuah0
drwx------  2 skrd skrd  4096 2011-11-25 15:31 .esd-1000
drwx------  2 gdm  gdm   4096 2011-11-25 15:31 .esd-112
drwx------  2 skrd skrd  4096 2011-11-25 15:31 .exchange-skrd
drwx------  2 skrd skrd  4096 2011-11-25 15:31 gpg-CVdpke
drwxrwxrwt  2 root root  4096 2011-11-25 15:31 .ICE-unix
drwx------  2 skrd skrd  4096 2011-11-25 15:31 keyring-Ej7Or4
drwx------  2 skrd skrd  4096 2011-11-25 15:39 orbit-skrd
drwx------  2 gdm  gdm   4096 2011-11-25 15:31 orbit-gdm
drwx------  2 root root  4096 2011-11-25 15:34 orbit-root
drwx------  2 skrd skrd  4096 2011-11-25 15:31 pulse-L55LxQdVaetE
drwx------  2 gdm  gdm   4096 2011-11-25 15:31 pulse-PKdhtXMmr18n
drwx------  2 skrd skrd  4096 2011-11-25 15:31 ssh-ZWNVnt1368
drwx------  2 skrd skrd  4096 2011-11-25 15:31 virtual-skrd.e6Skrh
-r--r--r--  1 root root    11 2011-11-25 15:31 .X0-lock
drwxrwxrwt  2 root root  4096 2011-11-25 15:31 .X11-unix

```

/root# ls -all
```


total 132
drwx------ 20 root root  4096 2011-09-08 14:45 .
drwxr-xr-x 21 root root  4096 2011-11-12 23:57 ..
drwx------  2 root root  4096 2011-11-12 23:57 .aptitude
-rw-------  1 root root  8544 2011-11-24 15:49 .bash_history
-rw-r--r--  1 root root  2227 2009-04-27 17:56 .bashrc
drwxr-xr-x  3 root root  4096 2010-10-03 02:25 .cache
drwx------  4 root root  4096 2011-03-14 18:59 .config
drwx------  3 root root  4096 2010-02-20 12:08 .dbus
drwxr-xr-x  2 root root  4096 2011-11-12 23:57 .debtags
drwxr-xr-x  2 root root  4096 2011-03-14 18:43 Desktop
-rw-------  1 root root    16 2010-02-20 12:17 .esd_auth
drwx------  3 root root  4096 2011-11-25 15:34 .gconf
drwx------  2 root root  4096 2011-11-25 15:34 .gconfd
drwx------  7 root root  4096 2011-08-14 14:16 .gnome2
drwx------  2 root root  4096 2010-02-20 12:08 .gnome2_private
drwxr-xr-x  2 root root  4096 2011-08-14 14:00 .gstreamer-0.10
drwx------  3 root root  4096 2011-03-14 18:59 .kde
drwx------  3 root root  4096 2010-10-30 00:05 .local
drwxr-xr-x  2 root root  4096 2011-03-14 18:43 .nautilus
-rw-r--r--  1 root root   140 2007-11-20 01:57 .profile
-rw-------  1 root root 26994 2011-09-08 14:45 .recently-used.xbel
drwxr-xr-x  3 root root  4096 2011-04-07 10:43 .subversion
drwx------  3 root root  4096 2011-10-14 00:47 .synaptic
drwx------  4 root root  4096 2011-08-11 15:18 .thumbnails
drwxr-xr-x  2 root root  4096 2009-10-29 05:05 .wapi

```

Boot info script results
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   272,446,334   272,444,287   7 HPFS/NTFS
/dev/sda2         272,446,335   488,392,064   215,945,730   5 Extended
/dev/sda5         272,446,398   479,524,184   207,077,787  83 Linux
/dev/sda6         479,524,248   488,392,064     8,867,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        58BC7C55BC7C2F9C                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        22b225d3-fa48-49a5-b0c8-d9de12767191   ext4                                     
/dev/sda6        390570ae-bdde-4522-8297-961644b8895f   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=skrd)
/dev/sda1        /media/58BC7C55BC7C2F9C  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
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
menuentry 'Ubuntu, with Linux 2.6.32-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
	linux	/boot/vmlinuz-2.6.32-35-generic root=UUID=22b225d3-fa48-49a5-b0c8-d9de12767191 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
	echo	'Loading Linux 2.6.32-35-generic ...'
	linux	/boot/vmlinuz-2.6.32-35-generic root=UUID=22b225d3-fa48-49a5-b0c8-d9de12767191 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-35-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22b225d3-fa48-49a5-b0c8-d9de12767191
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 58BC7C55BC7C2F9C
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=22b225d3-fa48-49a5-b0c8-d9de12767191 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=390570ae-bdde-4522-8297-961644b8895f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 139.6GB: boot/grub/core.img
 165.5GB: boot/grub/grub.cfg
 154.2GB: boot/initrd.img-2.6.32-35-generic
 150.8GB: boot/vmlinuz-2.6.32-35-generic
 154.2GB: initrd.img
 150.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

Does anyone have any idea what just happened? Am I in any danger?

Thank you to anyone who'll take the bother (--,)

---

