---
title: "Can only boot to memtest"
date: 2011-02-01
forum: General Help
---

### Post by jondodson on 2011-02-01
Hi

I've just done a routine update and it went a bit wrong.  Downloaded ok and the terminal did it's unpacking and updating thing, then it said I needed to reboot.  So I did, and now I can only boot into memtest.

I've had this before and the solution was to hold shift down at boot to force grub to appear, then pick a kernel and set it as default in startupmanager once ubuntu had loaded.

But no dice this time, I've tried holding the shift key down (using USB and ps2 keyboards) but I cant make grub appear - straight to memtest every time.

If anyone could help me get back to the gui, I'd be very grateful.

Cheers,
Jon

PS detail are: 10.4 LTS, always kept up to date.  Athlon 6000 x2 with 4gb, wifi only, 4850HD (ati drivers).  System rock solid for over a year prior to this.

---

### Post by jondodson on 2011-02-02
Anyone please?

---

### Post by Rubi1200 on 2011-02-02
Hi,
please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Thanks.

---

### Post by jondodson on 2011-02-02
Thank you for your reply.  I'm in a Live CD.  Here is the output from the script:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   964,703,249   964,701,202  83 Linux
/dev/sda2         964,703,250   976,768,064    12,064,815   5 Extended
/dev/sda5         964,703,313   976,768,064    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f14bee65-d5b5-476a-a707-db1badb1cd74   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        30058324-27a2-46c7-8f70-8948a85df263   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        d3995a14-7194-483f-a14d-16c8f818f97b   ext4       Data                          
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
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
set default="14"
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
search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
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
search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro splash vga=789 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro single splash vga=789 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro splash vga=789 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro single splash vga=789 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro splash vga=789 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro single splash vga=789 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro splash vga=789 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro single splash vga=789 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro splash vga=789 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro single splash vga=789 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro splash vga=789 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro single splash vga=789 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro splash vga=789 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f14bee65-d5b5-476a-a707-db1badb1cd74 ro single splash vga=789 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f14bee65-d5b5-476a-a707-db1badb1cd74
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=30058324-27a2-46c7-8f70-8948a85df263 none            swap    sw              0       0


=================== sda1: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/core.img
  43.3GB: boot/grub/grub.cfg
 141.8GB: boot/initrd.img-2.6.32-21-generic
 141.8GB: boot/initrd.img-2.6.32-22-generic
  42.7GB: boot/initrd.img-2.6.32-24-generic
   1.0GB: boot/initrd.img-2.6.32-25-generic
  31.9GB: boot/initrd.img-2.6.32-26-generic
   2.1GB: boot/initrd.img-2.6.32-27-generic
  43.6GB: boot/initrd.img-2.6.32-28-generic
 141.8GB: boot/vmlinuz-2.6.32-21-generic
    .3GB: boot/vmlinuz-2.6.32-22-generic
 142.0GB: boot/vmlinuz-2.6.32-24-generic
 142.0GB: boot/vmlinuz-2.6.32-25-generic
 142.0GB: boot/vmlinuz-2.6.32-26-generic
 142.0GB: boot/vmlinuz-2.6.32-27-generic
 142.0GB: boot/vmlinuz-2.6.32-28-generic
  43.6GB: initrd.img
   2.1GB: initrd.img.old
 142.0GB: vmlinuz
 142.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by Rubi1200 on 2011-02-02
Here is what I suggest:

The following procedure needs to be done from the LiveCD.

Please copy/paste the commands to avoid mistakes.

```
sudo mkdir /mnt/temp 

sudo mount /dev/sda1 /mnt/temp

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done

sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf

sudo chroot /mnt/temp
```This last command will give you a root prompt, therefore no need to preface commands with sudo.

I would start by trying some housecleaning;

```
apt-get autoclean
apt-get clean
apt-get update
apt-get upgrade
apt-get install -f
dpkg --configure -a
exit
```When you are finished, and assuming there were no errors, run this command to unmount and exit the chroot:

```
for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
```Reboot and see if you can get in.

If this does not work, I would try it again, but instead of housecleaning, try purging and reinstalling grub using the following commands:

```
apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc
update-grub 
exit
for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
```If this is not clear, please refer to this guide and/or ask before proceeding:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by jondodson on 2011-02-02
Hi & thanks for helping.  Unfortunately, neither method does it.  Both fail in a similar manner - with an 'abort' message when I select Y to continue.  Here's the terminal text of method 2 (like I say method 1 did the same thing):

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp 
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-pc* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 8,090kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.
root@ubuntu:/# 

```

---

### Post by jondodson on 2011-02-02
Rubi1200 - THANK YOU.  Solved by method two.  I was erroneously cut and pasting the whole block in but it wasn't processing anything after the the abort message.  I cut and pasted it in one line at a time and I have just rebooted into the GUI from sda1

Thanks again.):P

Jon.

---

### Post by Rubi1200 on 2011-02-03
No problem, you are more than welcome :-)

Glad you got things sorted out.

---

### Post by -::Bas::- on 2012-02-16
> **Rubi1200 said:**
> Here is what I suggest:

The following procedure needs to be done from the LiveCD.

Please copy/paste the commands to avoid mistakes.

```
sudo mkdir /mnt/temp 

sudo mount /dev/sda1 /mnt/temp

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done

sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf

sudo chroot /mnt/temp
```

I was a bit overambitious deleting old kernels and accidently deleted the kernel my server was running on.
After that, I too could only boot into memtest, but that was because I did not have any kernels installed. I only realised after updating my grub.

What I did to fix this was running the quoted code (my ubuntu is installed on sda1 as well) to chroot into my linux. Then I installed a kernel, by selecting matching headers and image. Then updated Grub, et voilá, I had a working kernel installed and can boot my server again :D

Thanks!!

---

