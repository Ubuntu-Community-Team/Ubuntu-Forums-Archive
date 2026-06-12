---
title: "I can't find the older kernels so I can delete them with Ubuntu Tweak"
date: 2010-03-31
forum: General Help
---

### Post by cezar_dan on 2010-03-31
I already know about Ubuntu Tweak but the list of kernels seems to show only my 9.10 kernels. I checked GRUB and the 9.10 kernels are linux 2.6.31-17 and 2.6.31-19 but (acording to GRUB) the ones I am looking for should be version 2.6.28-17.

What should I do? I really need the extra space.

---

### Post by konqueror7 on 2010-03-31
> **cezar_dan said:**
> I already know about Ubuntu Tweak but the list of kernels seems to show only my 9.10 kernels. I checked GRUB and the 9.10 kernels are linux 2.6.31-17 and 2.6.31-19 but (acording to GRUB) the ones I am looking for should be version 2.6.28-17.

What should I do? I really need the extra space.

hello! welcome to the forums! you can manually remove them in synaptic, as 'linux-headers-*'

---

### Post by cezar_dan on 2010-03-31
Thank you for the welcome:)

Unfortunately I still can't find what I'm looking for. All the installed packages are 2.6.31-17 or 2.6.31-19. I'm a bit apprehensive about deleting any kernel until I know for sure I won't break Ubuntu doing it. Shouldn't the ones I'm looking for be version 2.6.28?

---

### Post by byStanderone on 2010-03-31
kernel 2.6.28 is for jaunty...do you still have it installed in your system?

---

### Post by cezar_dan on 2010-03-31
Yes. It's the reason I want to find and delete that kernel. It's taking up precious disk space.

---

### Post by john newbuntu on 2010-03-31
Does:
sudo apt-get remove --purge linux-image-2.6.28-17
help?

---

### Post by plucky on 2010-03-31
Post output of ```
ls -l /boot
```

In synaptic search for **linux-image** and only the the ones with green boxes are installed.

Good Luck

---

### Post by cezar_dan on 2010-03-31
> **john newbuntu said:**
> Does:
sudo apt-get remove --purge linux-image-2.6.28-17
help?

Nope :(

It says that it couldn't find it. But I tried to run Ubuntu 9.04 and it still works. So I'm guessing the kernel is still there.

> **plucky said:**
> Post output of ```
ls -l /boot
```

In synaptic search for **linux-image** and only the the ones with green boxes are installed.

Good Luck

The kernel that is with a green box is the one for 9.10 . The one I'm trying to delete is the one for 9.04 which is missing from the list.

So far I have been trying to find the kernel for 9.04 while running 9.10. Should I start 9.04 and try to delete it from the inside? Is that even possible?

---

### Post by lordskid on 2010-03-31
is it possible that maybe you have jaunty installed in another partition?

---

### Post by konqueror7 on 2010-03-31
do you multi-boot maybe?

---

### Post by cezar_dan on 2010-03-31
> **lordskid said:**
> is it possible that maybe you have jaunty installed in another partition?

I'm not sure really. A friend first installed Jaunty from a CD then updated to Karmic via download. I'm not sure how it was installed after that.

> **konqueror7 said:**
> do you multi-boot maybe?

What is a multi-boot?

---

### Post by plucky on 2010-03-31
> I checked GRUB and the 9.10 kernels are linux 2.6.31-17 and 2.6.31-19 but (acording to GRUB) the ones I am looking for should be version 2.6.28-17.

Post the output of ```
ls -l /boot
``` as that is where the linux kernels are kept.

When you said you looked at Grub,what version of Grub did you have? 

The version of grub changed in Ubuntu 9.10,so knowing which grub you have is important.
Try these commands from a terminal ```
cat /boot/grub/menu.lst
cat /boot/grub/grub.cfg
``` Only one should work,so post the output from the one that works.

---

### Post by konqueror7 on 2010-03-31
could you maybe post the contents of your menu.lst?
```
cat /boot/grub/menu.lst
```

---

### Post by byStanderone on 2010-03-31
...just a thought, if you could still boot on jaunty, perhaps you can search for the old kernels from there using jaunty synaptic manager...should you find it or them, completely remove, reboot on karmic and do a sudo update-grub.

---

### Post by cezar_dan on 2010-04-03
**ls -l /boot** says:

```
total 27460 
-rw-r--r-- 1 root root  629446 2009-12-10 21:33 abi-2.6.31-17-generic 
-rw-r--r-- 1 root root  629446 2010-01-28 06:39 abi-2.6.31-19-generic 
-rw-r--r-- 1 root root  111371 2009-12-10 21:33 config-2.6.31-17-generic 
-rw-r--r-- 1 root root  111371 2010-01-28 06:39 config-2.6.31-19-generic 
drwxr-xr-x 2 root root    4096 2010-02-22 18:05 grub 
-rw-r--r-- 1 root root 7650133 2010-02-19 04:26 initrd.img-2.6.31-17-generic 
-rw-r--r-- 1 root root 7650303 2010-03-21 10:22 initrd.img-2.6.31-19-generic 
-rw-r--r-- 1 root root  128796 2009-10-23 19:11 memtest86+.bin 
-rw-r--r-- 1 root root 1665500 2009-12-10 21:33 System.map-2.6.31-17-generic 
-rw-r--r-- 1 root root 1665617 2010-01-28 06:39 System.map-2.6.31-19-generic 
-rw-r--r-- 1 root root    1196 2009-12-10 21:35 vmcoreinfo-2.6.31-17-generic 
-rw-r--r-- 1 root root    1196 2010-01-28 06:41 vmcoreinfo-2.6.31-19-generic 
-rw-r--r-- 1 root root 3890560 2009-12-10 21:33 vmlinuz-2.6.31-17-generic 
-rw-r--r-- 1 root root 3891264 2010-01-28 06:39 vmlinuz-2.6.31-19-generic
```

**cat /boot/grub/menu.lst** says:

```
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
default		0 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		10 

## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
#hiddenmenu 

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
# title		Windows 95/98/NT/2000 
# root		(hd0,0) 
# makeactive 
# chainloader	+1 
# 
# title		Linux 
# root		(hd0,1) 
# kernel	/vmlinuz root=/dev/hda2 ro 
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
# kopt=root=UUID=593fdb51-7048-4f8a-b75f-4a3676cdbf4b ro 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=593fdb51-7048-4f8a-b75f-4a3676cdbf4b 

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

title		Ubuntu 9.10, kernel 2.6.31-19-generic 
uuid		593fdb51-7048-4f8a-b75f-4a3676cdbf4b 
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=593fdb51-7048-4f8a-b75f-4a3676cdbf4b ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic 
quiet 

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) 
uuid		593fdb51-7048-4f8a-b75f-4a3676cdbf4b 
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=593fdb51-7048-4f8a-b75f-4a3676cdbf4b ro  single 
initrd		/boot/initrd.img-2.6.31-19-generic 

title		Ubuntu 9.10, kernel 2.6.31-17-generic 
uuid		593fdb51-7048-4f8a-b75f-4a3676cdbf4b 
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=593fdb51-7048-4f8a-b75f-4a3676cdbf4b ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic 
quiet 

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) 
uuid		593fdb51-7048-4f8a-b75f-4a3676cdbf4b 
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=593fdb51-7048-4f8a-b75f-4a3676cdbf4b ro  single 
initrd		/boot/initrd.img-2.6.31-17-generic 

title		Ubuntu 9.10, memtest86+ 
uuid		593fdb51-7048-4f8a-b75f-4a3676cdbf4b 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda6. 
title		Ubuntu 9.04, kernel 2.6.28-17-generic (on /dev/sda6) 
root		(hd0,5) 
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=307b37c6-d58a-4ac3-a7a5-00a9e2baaa1f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda6. 
title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda6) 
root		(hd0,5) 
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=307b37c6-d58a-4ac3-a7a5-00a9e2baaa1f ro single 
initrd		/boot/initrd.img-2.6.28-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda6. 
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6) 
root		(hd0,5) 
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=307b37c6-d58a-4ac3-a7a5-00a9e2baaa1f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda6. 
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6) 
root		(hd0,5) 
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=307b37c6-d58a-4ac3-a7a5-00a9e2baaa1f ro single 
initrd		/boot/initrd.img-2.6.28-11-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda6. 
title		Ubuntu 9.04, memtest86+ (on /dev/sda6) 
root		(hd0,5) 
kernel		/boot/memtest86+.bin  
savedefault 
boot
```

> **byStanderone said:**
> ...just a thought, if you could still boot on jaunty, perhaps you can search for the old kernels from there using jaunty synaptic manager...should you find it or them, completely remove, reboot on karmic and do a sudo update-grub.

I did think of something like that (the "deleting from the inside" I mentioned a few posts back) but I'm hesitating to mess with the kernel in any way. I'm no expert and I wouldn't like to brake something. Plus I'm not quite sure if it can be done. Wouldn't Jaunty simply crash if I just deleted the kernel?

---

### Post by drs305 on 2010-04-03
Are you using Grub2? And if so, is the reason you think you have the older kernels still on your machine because you see them in the Grub2 menu?

Grub2's menu is composed of kernels it finds, as well as entries in other menus. So it could be reading the menu.lst file and adding these entries even though they are no longer current. Try renaming the "menu.lst" file (if you are sure you aren't using Grub legacy 0.97) and then running "sudo update-grub". If the kernels aren't on your machine they should disappear from your Grub2 menu.

---

### Post by cezar_dan on 2010-04-03
The reason I think I still have the kernels is that I can still boot Jaunty if I so choose. Also, when I boot it it still has the same settings and software I installed in the limited time I used it (a few days) and none of the new software and settings from Karmic seem to be present.

If I think about it it would suggest that Jaunty is installed on another partition.

---

### Post by drs305 on 2010-04-03
Try locating it with the following (substitute kernel versions as desired):
```
locate vmlinuz-2.6.28-17
```
If nothing is found:
```
sudo find / -iname vmlinuz-2.6.28-17*
```

---

### Post by Gunman1982 on 2010-04-03
To make some things more clear:
You have a multiboot system, which means two or more (in your case two) systems you can boot independendly of each other.

> Ubuntu 9.10
root=UUID=593fdb51-7048-4f8a-b75f-4a3676cdbf4b
Ubuntu 9.04
root=UUID=307b37c6-d58a-4ac3-a7a5-00a9e2baaa1f
Would be nice if you could tell us which partitions you have by executing:
'sudo fdisk -l /dev/sda'
and what is mounted at the moment:
'mount'

---

### Post by cezar_dan on 2010-04-03
Sorry drs305 but both those commands (executed from Karmic) didn't do anything.

**sudo fdisk -l /dev/sda** said:

```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51415140

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1039     8345736   83  Linux
/dev/sda2            1040        4864    30724312+   f  W95 Ext'd (LBA)
/dev/sda5            1040        4274    25985106    7  HPFS/NTFS
/dev/sda6            4275        4831     4474071   83  Linux
/dev/sda7            4832        4864      265041   82  Linux swap / Solaris
```

**mount** said:
```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cezar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cezar)
/dev/sr1 on /media/VMCLite_9.3.6.12095_&#26956;_ type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda5 on /media/depozit type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

---

### Post by egalvan on 2010-04-03
Ýour grub/menu.lst boot files show

 9.10 mounted on sda1
 9.04 mounted on sda6

---

### Post by cezar_dan on 2010-04-03
Ok. Now how do I get rid of 9.04?

---

### Post by lidex on 2010-04-03
Boot into 9.04 and backup any needed data from that install.
Boot into 9.10 and run gparted from your "System>Administration" menu (may be called partition manager or some such). Right click on entry for sda6, hover over "format to" and select file system matching your 9.10 partitions (ext3 or ext4). Click the apply button. *[COLOR="Red"]WARNING: all data on that partition will be lost!![/COLOR]*. Once that's gone you'll have to boot into ubuntu LiveCD or gparted LiveCD to resize your remaining 9.10 partition and recover that space. It is recommended to backup or image a partition before resizing.
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

