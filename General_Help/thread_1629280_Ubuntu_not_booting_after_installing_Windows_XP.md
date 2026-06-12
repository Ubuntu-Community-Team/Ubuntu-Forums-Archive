---
title: "Ubuntu not booting after installing Windows XP"
date: 2010-11-23
forum: General Help
---

### Post by Punkristo on 2010-11-23
So I decided to install Windows XP on a second partition on my computer. Windows is loading fine but now I cannot boot from Ubuntu. Anybody knows how to fix this?

---

### Post by Quackers on 2010-11-23
Please boot from the Ubuntu Live cd and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply).
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by wilee-nilee on 2010-11-23
Post the generated text file that you get by running the bootscript in my signature. Come back to the thread open a reply click on the # in the reply panel and paste all the text from that file in between the code tags.

Doh follow the post above.;) Same information, this is where we start.

---

### Post by Punkristo on 2010-11-23
> **wilee-nilee said:**
> Post the generated text file that you get by running the bootscript in my signature. Come back to the thread open a reply click on the # in the reply panel and paste all the text from that file in between the code tags.

Doh follow the post above.;) Same information, this is where we start.

How do I open a .SH file on windows?

---

### Post by topsecret on 2010-11-23
> **Punkristo said:**
> So I decided to install Windows XP on a second partition on my computer. Windows is loading fine but now I cannot boot from Ubuntu. Anybody knows how to fix this?
hi 
its very easy 
boot from the Dvd or cd again (which contains Ubuntu) and choose "try Ubuntu"
then use the Application/Tools/Terminal and write this:
```
sudo su
```
to know in which Partition is ur Ubuntu write this:
```
sudo fdisk -l /dev/sda
```
if ur harddrive is sata:
```
sudo fdisk -l /dev/hda
```
u will get something like this Picture
[IMG]http://www.linuxac.org/forum/attachment.php?attachmentid=9859&stc=1&d=1259654582[/IMG]
now u know where is ur linux !! in this picture is sda8 so write this:
```
sudo mount /dev/sda8 /mnt
```
then write this to repaire the bootloader(grub2):
s```
udo grub-install --root-directory=/mnt/ /dev/sda
```
congratulation its done :popcorn:

---

### Post by Hippytaff on 2010-11-23
I think all that needs to happen to repair your ubuntu install is
You need to boot from livecd or usb and do the following in the terminal 
 ```

 sudo fdisk -l
 
```
 remember what your root partition is called (usually sda5)...it will be  the one that says Linux (just Linux, not swap or solaris etc)
 then
 ```

 sudo mount /dev/sda5 /mnt
 
```
 ```

 sudo mount /dev/sda5 /mnt/boot
 
```
 here I'm assuming your root partition is sda5
 
 mount the rest of your devices
 ```

 sudo mount --bind /dev /mnt/dev

```

now
```

sudo chroot /mnt

```
```

sudo update-grub

```
install grub to mbr (master boot record)
```

grub-install /dev/sda

```
 any errors at this point do
```

grub-install --recheck /dev/sda

```
press ctrl+D
```

sudo unmount /mnt/dev

```
```

sudo unmount/mn

```
 and restart your pc
Now XP should be missing, that's fine, boot into ubuntu and in a terminal type
```

sudo update-grub

```
and then
```

sudo grub-install /dev/sda

```
all should be fixed...but please follow Quackers et al's advice, I've  only done this once :-) they do this kind of thing all the time :-)

---

### Post by wilee-nilee on 2010-11-23
> **Punkristo said:**
> How do I open a .SH file on windows?

First disregard post 5&6 it doesn't provide enough information, and is acting before having enough information. For example you may have grub-legacy not grub2

Boot a live Ubuntu cd to run this click on the bootscript link it explains the process,  but feel free to ask more questions. 

No matter what even if you have just had a wubi install you should have a corresponding distro's live cd. I see the second partition reference but I want to see the hard facts.

---

### Post by Punkristo on 2010-11-23
These were the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   224,827,391   224,825,344  83 Linux
/dev/sda2    *    224,829,675   234,420,479     9,590,805   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2002 MB, 2002780160 bytes
16 heads, 32 sectors/track, 7640 cylinders, total 3911680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     3,911,679     3,903,616   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9b43ba79-a461-4707-9b6b-128c8e5b5d36   ext4                                     
/dev/sda2        C2E4BF84E4BF796D                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A99E-1B22                              vfat       PUBLIC                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/PUBLIC            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set 9b43ba79-a461-4707-9b6b-128c8e5b5d36
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
search --no-floppy --fs-uuid --set 9b43ba79-a461-4707-9b6b-128c8e5b5d36
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
	search --no-floppy --fs-uuid --set 9b43ba79-a461-4707-9b6b-128c8e5b5d36
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=9b43ba79-a461-4707-9b6b-128c8e5b5d36 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9b43ba79-a461-4707-9b6b-128c8e5b5d36
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=9b43ba79-a461-4707-9b6b-128c8e5b5d36 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9b43ba79-a461-4707-9b6b-128c8e5b5d36
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=9b43ba79-a461-4707-9b6b-128c8e5b5d36 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9b43ba79-a461-4707-9b6b-128c8e5b5d36
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=9b43ba79-a461-4707-9b6b-128c8e5b5d36 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9b43ba79-a461-4707-9b6b-128c8e5b5d36
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9b43ba79-a461-4707-9b6b-128c8e5b5d36 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9b43ba79-a461-4707-9b6b-128c8e5b5d36
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9b43ba79-a461-4707-9b6b-128c8e5b5d36 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9b43ba79-a461-4707-9b6b-128c8e5b5d36
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9b43ba79-a461-4707-9b6b-128c8e5b5d36
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
# / was on /dev/sda1 during installation
UUID=9b43ba79-a461-4707-9b6b-128c8e5b5d36 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ede6574e-8d39-4102-bfbb-9f209d2280b2 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 111.8GB: boot/grub/core.img
  52.7GB: boot/grub/grub.cfg
 111.9GB: boot/initrd.img-2.6.32-21-generic
 112.0GB: boot/initrd.img-2.6.32-24-generic
  15.0GB: boot/initrd.img-2.6.32-25-generic
 111.8GB: boot/vmlinuz-2.6.32-21-generic
 112.0GB: boot/vmlinuz-2.6.32-24-generic
 112.0GB: boot/vmlinuz-2.6.32-25-generic
  15.0GB: initrd.img
 112.0GB: initrd.img.old
 112.0GB: vmlinuz
 112.0GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff

```

---

### Post by Hippytaff on 2010-11-23
> **wilee-nilee said:**
> First disregard post 5&6 it doesn't provide enough information, and is acting before having enough information.

Boot a live Ubuntu cd to run this click on the bootscript link it explains the process,  but feel free to ask more questions. 

No matter what even if you have just a wubi install you should have a corresponding distro's live cd.

Fair enough...you are the esxperts, this worked for me when I installed xp after ubuntu...it's there if the op needs it if you think he needs to :-)

---

### Post by wilee-nilee on 2010-11-23
> **Hippytaff said:**
> Fair enough...you are the esxperts, this worked for me when I installed xp after ubuntu...it's there if the op needs it if you think he needs to :-) Yes but as we see now Linux is in sda1. About the only thing I'm a expert in as having a slacker lifestyle. The script just generally should be the default thing thing to look at

Thread starter hold on while I and Quackers read the script.

---

### Post by Quackers on 2010-11-23
It may be enough to open a terminal from the Live cd and run
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Then reboot and see if Ubuntu boots ok. If it does run ```
sudo update-grub
``` in a terminal and watch as grub.cfg is configured to see if Windows XP is listed.
If Ubuntu won't boot it may be necessary to chroot into your installation later.
Does willee-nillee concur?

---

### Post by wilee-nilee on 2010-11-23
So you have no swap anymore just so you know. From a live Ubuntu cd run these two command then reboot to Ubuntu and run sudo update-grub.

```
sudo mount /dev/sda1 /mnt
```

Then

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

reboot to the Ubuntu **install** and run.
```
sudo update-grub
```

Doh, good job Quackers, as you will see OP our commands are identical, as pretty much the same as the others posted except we have it pointed at the correct partition. Thanks for posting the script, it just makes life easier for all of us.

---

### Post by Punkristo on 2010-11-23
Now is booting Ubuntu again but it's not letting me choose if I wanna boot from Windows.

---

### Post by Quackers on 2010-11-23
Have you run sudo update-grub in a terminal? Was Windows mentioned as grub.cfg was configured (in the terminal window)?

---

### Post by Hippytaff on 2010-11-23
now you just need to open a terminal and do
```

sudo update-grub

```
I think :-s
willee-nillee, quackers?

---

### Post by wilee-nilee on 2010-11-23
> **Quackers said:**
> Have you run sudo update-grub in a terminal? Was Windows mentioned as grub.cfg was configured (in the terminal window)?

Probably needs a chkdsk if this doesn't work what do you think. All the XP boot stuff is in the menu.

---

### Post by Quackers on 2010-11-23
XP boot files look ok, but maybe grub overwrote it. It may need fixmbr to be run from the Windows repair disc.

---

### Post by Punkristo on 2010-11-23
Ok is working now, I just forgot that I needed to restart the computer again. Thanks a million! I really appreciate the help.

---

### Post by Quackers on 2010-11-23
Nice one :-)

---

### Post by wilee-nilee on 2010-11-23
Yipee a happy ending.;) Hey thanks for everyones help here.

Time for a cig for me always after a happy ending.;)

---

### Post by Hippytaff on 2010-11-23
Glad you managed to sort it - remember to mark the thread as solved in in the forum tools at the top of the page so others can benefit from what you did :-)

Nice one Quackers and Willee-nillee I learned a lot from this too :-)

---

