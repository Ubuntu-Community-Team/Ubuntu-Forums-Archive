---
title: "Dual Boot starting with ubuntu"
date: 2011-05-31
forum: General Help
---

### Post by RFRFG on 2011-05-31
i've seen many guides on how to create a dual boot of windows and linux when starting with windows, but i haven't found a guide to help with creating a windows partition to dual boot. i am currently running ubuntu and i have an xp iso, ripped from my cd on a desktop computer (don't have a cd drive). my hard drive is partitioned into the primary partition, extended, and linux swap. i've downloaded the gnome partition editor and it wont let me resize my partition. i tried "create partition table, but it says "2 partitions are currently active on device /dev/sda." so i can swap off one, but i can't alter the other at all. any help would be apriciated.

---

### Post by jerrrys on 2011-05-31
you have to unmount the hdd to partition it.  you don't have a cd drive?  can you boot from usb?

---

### Post by RFRFG on 2011-05-31
thank you for your response. i may be able to do it from a usb drive. when i attempt to unmount, i get this message: The partition 


Could not unmount /dev/sda1

could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

---

### Post by RFRFG on 2011-05-31
i can also use an external hard drive to install from, but not to boot off of as i have very limited time to use it

also, is it safe to delete the "extended" and "linux swap" partitions?

---

### Post by garvinrick4 on 2011-05-31
As long as you are not working on a drive that is mounted you are OK.

---

### Post by garvinrick4 on 2011-05-31
See keys in gparted that means they are mounted and cannot be worked on.

---

### Post by jerrrys on 2011-05-31
could you post a pic of your partitions, to be sure, thanks

---

### Post by RFRFG on 2011-05-31
[IMG]http://tdoui.webs.com/Screenshot.png[/IMG]i understand, but i keep getting this message when trying to unmount it

---

### Post by jerrrys on 2011-05-31
you have 45gig of data on your primary partition (sda1), whats with that?

---

### Post by RFRFG on 2011-05-31
it was experimentation with a virtual machine, i have about 20 gigs free now

---

### Post by garvinrick4 on 2011-05-31
> you have 45gig of data on your primary partition (sda1), whats with that?Hi jerrys,
 Looks like OP has about 41 gig of /home going on, does not have a seperate /home.
Maybe OP has it all backed up and wants to make a new partition for XP who really knows
only got about 8 gig left on drive. EDIT: just saw OP's last post he has 20 gig to play with.

RFRFG: make sure you got your stuff backed up before you start playing with partition table
or you are likely to lose it.
```
sudo parted -l
``` (lower case L)
This will give partitions in gigs.
##Have a nice day.

---

### Post by jerrrys on 2011-05-31
back to your question in post#4.  if you don't have ubuntu installed, then you have no use for swap or the extended partition.  so yes, wipe it if you want.

---

### Post by RFRFG on 2011-06-01
ubuntu is my current os.

i've learned that my bios is capable of booting from a usb drive, and i have a compatible usb drive to boot from, but when i tried setting it up (it was suggested to remove hard drives first and install to usb drive) on my PC, it wouldn't boot my altered CD (i must have done something wrong) and now my PC booting is out of order. so now i have another problem... i was using these directions: [http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf]("http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf")

---

### Post by garvinrick4 on 2011-06-01
Run this script in a live cd or usb:
download script to DESKTOP and then run this line of code in a terminal will put a file
on desktop called RESULTS copy and paste here. After copied here highlight whole thing
and hit the # in upper right or Message box will be easier to read bootscript.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
  sudo bash ~/Desktop/boot_info_script.sh
```

---

### Post by RFRFG on 2011-06-01
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   112,332,799   112,330,752  83 Linux
/dev/sda2         112,334,846   117,209,087     4,874,242   5 Extended
/dev/sda5         112,334,848   117,209,087     4,874,240  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        97ca4230-db32-43b4-972c-d4414d1ec8b2   ext4       
/dev/sda5        53298d50-80dd-4090-85d6-a31ca2547c2a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 97ca4230-db32-43b4-972c-d4414d1ec8b2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 97ca4230-db32-43b4-972c-d4414d1ec8b2
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 97ca4230-db32-43b4-972c-d4414d1ec8b2
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 97ca4230-db32-43b4-972c-d4414d1ec8b2
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=97ca4230-db32-43b4-972c-d4414d1ec8b2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 97ca4230-db32-43b4-972c-d4414d1ec8b2
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=97ca4230-db32-43b4-972c-d4414d1ec8b2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 97ca4230-db32-43b4-972c-d4414d1ec8b2
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=97ca4230-db32-43b4-972c-d4414d1ec8b2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 97ca4230-db32-43b4-972c-d4414d1ec8b2
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=97ca4230-db32-43b4-972c-d4414d1ec8b2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 97ca4230-db32-43b4-972c-d4414d1ec8b2
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=97ca4230-db32-43b4-972c-d4414d1ec8b2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 97ca4230-db32-43b4-972c-d4414d1ec8b2
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=97ca4230-db32-43b4-972c-d4414d1ec8b2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 97ca4230-db32-43b4-972c-d4414d1ec8b2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 97ca4230-db32-43b4-972c-d4414d1ec8b2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=97ca4230-db32-43b4-972c-d4414d1ec8b2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=53298d50-80dd-4090-85d6-a31ca2547c2a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  18.134620667 = 19.471900672   boot/grub/core.img                             1
   2.363983154 = 2.538307584    boot/grub/grub.cfg                             1
  18.331218719 = 19.682996224   boot/initrd.img-2.6.32-21-generic              1
  18.458515167 = 19.819679744   boot/initrd.img-2.6.35-28-generic              1
  36.505313873 = 39.197282304   boot/initrd.img-2.6.38-8-generic               2
  18.264194489 = 19.611029504   boot/vmlinuz-2.6.32-21-generic                 1
  18.335220337 = 19.687292928   boot/vmlinuz-2.6.35-28-generic                 1
   1.829406738 = 1.964310528    boot/vmlinuz-2.6.38-8-generic                  1
  36.505313873 = 39.197282304   initrd.img                                     2
  18.458515167 = 19.819679744   initrd.img.old                                 1
   1.829406738 = 1.964310528    vmlinuz                                        1
  18.335220337 = 19.687292928   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  72 72 72 72 72 72 72 72  72 72 72 72 72 72 72 72  |rrrrrrrrrrrrrrrr|
*
000001b0  72 72 72 72 72 72 72 72  72 72 72 72 72 72 00 fe  |rrrrrrrrrrrrrr..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 4a 00 00 00  |...........`J...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by garvinrick4 on 2011-06-01
We are going to purge and then reinstall grub to mbr:
Put in Live Cd or Usb and use Try Ubuntu and with internet working. (firefox works to get online)
Now copy and paste these one at a time.
```

[CODE]sudo mount /dev/sda1 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done 
``````
sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf
``````
sudo chroot /mnt
``````
apt-get update
```Should get update with no errors, if errors your internet was not working in live cd or usb
```
apt-get purge grub grub-common grub-pc
``````
apt-get install grub-common grub-pc
```Use tab to toggle and say OK to put in sda
```
grub-install /dev/sda
``` above redundant but just in case
```
update-grub
``````
exit
``````
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
``````
sudo umount /mnt
``````
sudo reboot
```[/code]A few redundant commands but just want to make sure it is in sda and updated.

---

### Post by RFRFG on 2011-06-01
i'm sorry, what do you mean by live cd or usb?

---

### Post by garvinrick4 on 2011-06-01
> **RFRFG said:**
> i'm sorry, what do you mean by live cd or usb?
A install CD of Ubuntu and use Try Ubuntu instead of install Ubuntu when it asks.
Will then go to a Ubuntu desktop and in upper right hand corner is network applet
get your internet going and then you can open a terminal to copy and paste each line
of code by:  ctrl/alt/t   :at same time and terminal will pop up.

## Put CD in tray and reboot so it boots off of Cd and then choose Try Ubuntu:
Better to ask question than do it wrong, Ok. Or the USB flash drive.

---

### Post by garvinrick4 on 2011-06-01
how did you get the bootscript? What did you use? If you are booting and using the 60 gig
drive, let me know. That is all I see in bootscript, I think you are capable of booting into your
Hard drive. If you are let me know.

---

### Post by garvinrick4 on 2011-06-01
> **RFRFG said:**
> ubuntu is my current os.

i've learned that my bios is capable of booting from a usb drive, and i have a compatible usb drive to boot from, but when i tried setting it up (it was suggested to remove hard drives first and install to usb drive) on my PC, it wouldn't boot my altered CD (i must have done something wrong) and now my PC booting is out of order. so now i have another problem... i was using these directions: [http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf](http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf)

[http://ubuntuforums.org/showthread.php?t=1773239](http://ubuntuforums.org/showthread.php?t=1773239)

---

### Post by RFRFG on 2011-06-01
no cd drive... how do i do it on my usb drive?

---

### Post by garvinrick4 on 2011-06-01
There is a way to make a USB live drive. But first what are you using right now? Can you
boot into your Ubuntu on the 80 gig drive?

---

### Post by RFRFG on 2011-06-02
if i understand you correctly i believe that's what i do already...


and at the risk of sounding like a complete numbskull, is it possible to take the windows folder from a windows installed computer and copy it to the root directory of the usb drive to boot that way?

---

### Post by garvinrick4 on 2011-06-02
> is it possible to take the windows folder from a windows installed  computer and copy it to the root directory of the usb drive to boot that  way?I thought you goofed up your internal drive messing with it. If it is Windows instructions
for loading on a USB drive I have not done this before I work 99% of my time in Ubuntu
installs. I have used windows as a dual boot on sda drive because it is there when you purchase your machine. 
To install on a USB drive and its installer methods I do not know.
Try a Windows Forum where that is what they work with. Sorry I could not help you. Lots of
users do that so cannot be hard to Google search I would imagine. Have a nice day.

---

### Post by RFRFG on 2011-06-04
another set of quick questions... 

i don't see how it could be done, but is it possible to boot from an iso file? 
is it possible to make a usb drive emulate a cd-rom for bios?
is there a way to execute the windows installer from an iso on linux without using wine? (doesn't recognize partitions)

---

