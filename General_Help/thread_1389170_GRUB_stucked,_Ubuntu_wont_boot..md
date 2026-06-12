---
title: "GRUB stucked, Ubuntu wont boot."
date: 2010-01-24
forum: General Help
---

### Post by vicarus on 2010-01-24
hi to all, 

I am new to this forum, please guide me through if i made any mistakes. 

alright, here is my problem, some days ago i installed ubuntu 9.04 jaunty, and yesterday i perform an update as it is necessary to do so in order to upgrade to 9.10 the latest stable release. After the update, it required a reboot, i did tat, and as always i went to boot manually from my second hard drive where GRUB is installed.

Then here comes the problem, normally my computer would display the volume of HDD and other stuff on a black screen (not sure if that is the POST screen) and then at the bottom it will show GRUB and it continues to run and boot ubuntu. This time, however, it shows GRUB and it stop right there, no more commands no movement at all. i tried Control + Alt + F2, nothing happened, all keyboard input seems to be not working, except for Control + Alt + Delete, which restarts the computer.

BTW, i am having 2 HDD in my system unit, Vista and Ubuntu. (Vista was installed first long before Ubuntu)

Anyone out there with any kinda of solutions please help. Thank you!

---

### Post by Jackzor on 2010-01-24
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Try this

---

### Post by akhilbehl on 2010-01-24
hey maybe .. you did not allow grub to change the menu.lst during the installation??
that is why grub is not able to boot your update kernel.

i suggest that you get a live cd and boot into your machine..change to your root..

Run Alt+F2 > gnome-terminal

commands are:

sudo fdisk -l

Check which one is your boot partition.. since you say it is the second hard drive it must be /dev/sdbX (X being the partition number). However it can also be /dev/sdaX. ( here /dev/sdA,B,C etc. denotes the number of the HDD as detected by your live CD.) Once you find it out, say /dev/sdb1, do:

sudo mount /dev/sdb1 /mnt
sudo mount -o bind /dev /mnt
sudo mount -o bind /proc /mnt

sudo chroot /mnt

and post the contents of the file /boot/grub/menu.lst on this thread.. 

cat /boot/grub/menu.lst

i am sure you will get help soon.. it should be easier..

if you are using grub2 instead.. then it is all the more easier.

after changing to your root.. just do..

sudo grub-install

sudo update-grub

get out of the root folder

by typing 'exit' at the terminal and reboot.

---

### Post by akhilbehl on 2010-01-24
oh.. crap.. just realised that the person above me has posted almost similar instructions in the link.. sorry for the repitition.

---

### Post by vicarus on 2010-01-24
GRUB shld be in hdb1 because i did fixmbr for some reason after installing ubuntu, and i gave the computer the link to store GRUB. shld be in second drive first partition, hdb1. 

i am not using GRUB2 caz my verison is 9.04 where grub2 is not available yet in that cd. 

and it stucked at the screen right after POST, where that screen shows HDD and some PCI devices stuff. just hope tat this info might help in getting solution.

---

### Post by vicarus on 2010-01-24
ok, problemo sloved, tried jackzor's link and it worked, at least i am replying using ubuntu. But it is kinda strange, when i boot it, there is 5 options for ubuntu the other one is vista which wont boot even if i choose it, i dono y.. 

anyway, thx guys, and, ermm.. is there anything tat i need to do to make sure that these stuff wont happen again? because it seems like after i reinstall GRUB, there is 2 more extra option at the boot menu, i dun wanna keep reinstalling every time i update ubuntu and getting more and more options at the boot menu...

thx anyway.

---

### Post by akhilbehl on 2010-01-24
you don't have to keep all the options..

you can go to /boot/grub/menu.lst
and comment out the kernels that you do not want listed in the grub menu.

as per the Vista entry, i am just taking a guess.. from your first post it seems your vista partition is on the first HDD.

your grub might be finding for it in the second hard drive. it might help if you could post your menu.lst and sudo fdisk -l output here..

otherwise you can google how to edit menu.lst, you will surely find a lot of good documentation.

---

### Post by vicarus on 2010-01-25
This is my menu.lst :

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
# kopt=root=UUID=d2a228fd-94a5-4ece-80dd-406b9591ee64 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d2a228fd-94a5-4ece-80dd-406b9591ee64

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		d2a228fd-94a5-4ece-80dd-406b9591ee64
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=d2a228fd-94a5-4ece-80dd-406b9591ee64 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		d2a228fd-94a5-4ece-80dd-406b9591ee64
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=d2a228fd-94a5-4ece-80dd-406b9591ee64 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d2a228fd-94a5-4ece-80dd-406b9591ee64
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d2a228fd-94a5-4ece-80dd-406b9591ee64 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d2a228fd-94a5-4ece-80dd-406b9591ee64
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d2a228fd-94a5-4ece-80dd-406b9591ee64 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d2a228fd-94a5-4ece-80dd-406b9591ee64
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------------------------------------------

And this is my sudo fdisk -l :

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2db6852a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35999   289155072    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           35999       60802   199229440    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5134ee39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       34693   278668945+  83  Linux
/dev/sdb2           34693       60802   209715200    7  HPFS/NTFS

--------------------------------------------------------------------------------------------------------------------

It seems to be strange tat my Vista is known as Windows Vista (Loader). I mean why loader... and the worse part is when i try to install Ubuntu, i selected manual partition option, and it says "There is no Operating System in this computer." at the very top of the installation application..

Something is wrong with my Windows?

and erm, i am still a novice using Ubuntu although i know a little computing but Ubuntu is really new to me.

---

