---
title: "Ubuntu only boots to memtest86+"
date: 2009-07-02
forum: General Help
---

### Post by hgolden on 2009-07-02
I have been using Ubuntu 9.04 for a while now and everything worked fine until I turned on my computer today

Everything loads fine, gets to the grub initialization and then goes right into memtest86+.  It completed without errors, but the GUI never loads!

When I press esc to see the grub menu, only "Ubuntu 9.04, memtest86+" is shown.

I checked the HDD from the BIOS and everything was fine, I have no idea how to fix this problem

FYI, I am using a Lenovo T61

---

### Post by blueridgedog on 2009-07-03
Can you boot on a liveCD?

If so, mount your internal disk and post the output of:

```
ls /mnt/disk/boot

cat /mnt/disk/boot/grub/menu.lst
```

Substiture /mnt/disk for where your disk gets mounted.

If you need help mounting your internal disk, then can you post the output of:

```
sudo fdisk -l

mount
```

With the output of these, I or others can get you to the next step.

---

### Post by hgolden on 2009-07-03
```
ubuntu@ubuntu:~$ cat /media/disk/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bdf8dd9d-afcd-4379-971f-61cfea784954 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bdf8dd9d-afcd-4379-971f-61cfea784954

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, memtest86+
uuid        bdf8dd9d-afcd-4379-971f-61cfea784954
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by blueridgedog on 2009-07-03
Can you post the output of 

```
ls /media/disk/boot
```

It appears from your menu.lst that you don't have any kernels setup.  She should be able to fix that if we can see what kernel you have to boot.

It may be an error or a glitch in an upgrade and should be repairable.

---

### Post by hgolden on 2009-07-03
```
ubuntu@ubuntu:~$ ls /media/disk/boot
grub memtest86+.bin

```

---

### Post by blueridgedog on 2009-07-03
I find it odd that you don't have a kernel in your boot directory.  You should have vmlinuz-2.6.28-11-generic.

Can you tell me more about what happened just before your system started booting into memtest?

I see two paths forward, one is to force install the kernel after booted from the liveCD using chroot, and the other is to manually get the kernel you need and place it in /boot and edit /boot/grub/menu.lst.

Perhaps another forum user will post an alternative I have not considered.

---

### Post by hgolden on 2009-07-03
Thanks, the last thing I did was sudp apt-get install libdb4.3 (or something like that) because I kept getting an authentication error with that coming up.  Everything was working fine afterwards.  It was only when I shutdown a few hours later and then started up again when the boot problem occured.

How would I go about either of those two paths, and which one is probably the best?

---

### Post by blueridgedog on 2009-07-03
If you are booting off of the Jaunty liveCD, can you tell me what kernel is on it?  What is in /boot?

---

### Post by hgolden on 2009-07-03
```
ubuntu@ubuntu:~$ ls /boot
abi-2.6.28-11-generic     System.map-2.6.28-11-generic
config-2.6.28-11-generic  vmcoreinfo-2.6.28-11-generic
memtest86+.bin

```

---

### Post by blueridgedog on 2009-07-03
Can you post the output of the following commands?

```
sudo fdisk -l
```

and 

```
mount
```

I will try and talk you through mounting your existing file system as the root file system once booted on the CD then installing the kernel.

Also, can you confirm that this is not a wubi install?

---

### Post by hgolden on 2009-07-03
This is not a wubi install.
Here are the outputs of the commands you requested:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4978ffc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x235431fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS


ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
ubuntu@ubuntu:~$ 
```

---

### Post by blueridgedog on 2009-07-03
OK, The overall plan is to  mount sda1 as your root file system while running on the live CD, then to force the install of a kernel, editing menu.lst when we have it installed.

First:  Change the root fs to your existing drive:

```
sudo mount --bind /dev /media/disk/dev
sudo chroot /media/disk
```

Now, install a new kernel:

```
sudo apt-get install linux-image-2.6.28-11-generic
```

If it complains, try
```

sudo apt-get install --reinstall linux-image-2.6.28-11-generic
```

If it still complains, post back.

Once installed, take a look in /media/disk/boot and you should have:

abi-2.6.28-11-generic
System.map-2.6.28-11-generic
config-2.6.28-11-generic
vmcoreinfo-2.6.28-11-generic
vmlinuz-2.6.28.11-generic

The next step is to place an entry into your menu.lst to boot the kernel:

```
gksudo gedit /media/disk/boot/grub/menu.lst
```

Between these two lines:
```

## ## End Default Options ##

title        Ubuntu 9.04, memtest86+
```

Add the following:


```
title		Ubuntu 9.04 kernel 2.6.28-11-generic
uuid		bdf8dd9d-afcd-4379-971f-61cfea784954
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bdf8dd9d-afcd-4379-971f-61cfea784954 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
```

This option will be the first option and will be booted prior to memtest.

A re-install may ultimately be in order, but I hope we can get you working again.

---

### Post by hgolden on 2009-07-03
wonderful, it all worked!  thank you so much!


just note:  i had to open a new terminal window to edit menu.lst, and the directory is 
gksudo gedit /media/disk/boot/grub/menu.lst

rather than
gksudo gedit /media/boot/grub/menu.lst

---

### Post by blueridgedog on 2009-07-03
Sorry about the typo, leaving "disk" out, but you caught it.  I am glad you are up and running.

---

### Post by boogers on 2009-09-10
Hi,  Great post.  I am having the same issue,  but when I 
  ```
sudo apt-get install linux-image-2.6.28-11-generic
```
i get this in return
```
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mencoder
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wireless-crda
Suggested packages:
  fdutils linux-doc-2.6.28 linux-source-2.6.28
The following NEW packages will be installed:
  linux-image-2.6.28-11-generic wireless-crda
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.6MB of archives.
After this operation, 95.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main wireless-crda 1.7
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main linux-image-2.6.28-11-generic 2.6.28-11.42
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/wireless-crda/wireless-crda_1.7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/wireless-crda/wireless-crda_1.7_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.28-11-generic_2.6.28-11.42_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.28-11-generic_2.6.28-11.42_i386.deb)  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

I am getting a solid internet connection though.  I dunno.  Thanks
this only happens after im in root@ubuntu

---

### Post by miklcct on 2009-09-11
If you're using DHCP, try to run
```

sudo dhclient

```

---

### Post by mswarbri on 2009-10-07
I've read this post with great interest as I seem to have suffered exactly the same issue after a partial upgrade recently. The Solution also seems straightforward enough until near the end in my case whereby I get the following failure ....

root@ubuntu:/# apt-get install --reinstall linux-image-2.6.28-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-2.6.28-11-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-image-2.6.28-11-generic has no installation candidate
root@ubuntu:/# 

This occure using the install or install reinstall approach.

Thx

---

### Post by acambre on 2009-12-02
Thanks for these instructions!!

A helpful note: I am on 9.04 server, and the instructions for this LiveCD don't appear to work. I was able to get into a recovery mode and load a console, and in doing that I didn't need to mount anything, so it took me a few minutes to realize that /media/disk doesn't apply to me.

---

