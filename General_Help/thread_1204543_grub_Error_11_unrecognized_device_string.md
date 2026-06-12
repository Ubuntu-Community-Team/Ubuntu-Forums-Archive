---
title: "grub Error 11: unrecognized device string"
date: 2009-07-04
forum: General Help
---

### Post by G_man on 2009-07-04
Hi I have this problem which came out from no where. I installed Ksplice and had some problems with updates and the system reacts like I am using it with more than 1 user. Then, I rebooted my laptop and faced this problem. I tried editing the string with no use. I am using ubuntu 9.04 and it is the only OS I am using. I don't know what I should edit the string to or what is making this problem. I have one partition I'm my only hard drive (dev/sda1)

Please help me.

---

### Post by G_man on 2009-07-06
Anybody?

---

### Post by lindsay7 on 2009-07-06
Did you install grub2 by any chance?


Are there any external drives connected to this computer?

---

### Post by G_man on 2009-07-07
No I did not install it. And Sometimes I connect my sdcards using the builtin card reader or with another card reader. I am writing to you with the same machine using an ubuntu live cd and able to see and use all of my files

---

### Post by lindsay7 on 2009-07-07
It could be a problem with the grub file. Lets reinstall it and see if that fixes it. Type these commands in the terminal from the live cd.

Originally Posted by lindsay7 View Post
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
__________________

---

### Post by G_man on 2009-07-07
Just did it. Will reboot now and see what will happen. Thanks

---

### Post by G_man on 2009-07-07
Did not work:

Typed:
grub> "find /boot/grub/stage1"
and got (hd0,0)

Typed:
grub> "root (hd0,0)"
and got no errors

Typed:
grub> "setup (hd0)"
and got:
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... suc

rebooted and got same error:

tried to type: 
grub> "setup (hd0,0)"
But got:
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
[COLOR="Red"] Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)[/COLOR]
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

will reboot and try again

---

### Post by G_man on 2009-07-07
Did not work :(

---

### Post by lindsay7 on 2009-07-07
Ok, lets see what you grub menu looks like,

Type sudo gedit /boot/grub/menu.lst  ( the letter l not the number 1) in the terminal and post the results.  No not change anything in the file just copy the results and close the file.

---

### Post by G_man on 2009-07-07
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
timeout		3

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
# kopt=root=UUID=dd89765a-440f-4852-8960-f5cc536a33b1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd89765a-440f-4852-8960-f5cc536a33b1

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
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title		Debian GNU/Linux, kernel 2.6.28-13-generic
root		dd89765a-440f-4852-8960-f5cc536a33b1
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd89765a-440f-4852-8960-f5cc536a33b1 ro quiet splash
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-13-generic (recovery mode)
root		dd89765a-440f-4852-8960-f5cc536a33b1
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=dd89765a-440f-4852-8960-f5cc536a33b1 ro single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic
root		dd89765a-440f-4852-8960-f5cc536a33b1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd89765a-440f-4852-8960-f5cc536a33b1 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root		dd89765a-440f-4852-8960-f5cc536a33b1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd89765a-440f-4852-8960-f5cc536a33b1 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel memtest86+
root		dd89765a-440f-4852-8960-f5cc536a33b1
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by lindsay7 on 2009-07-07
I look through every line of your grub menu and I can not find anything that looks wrong. Hopefully someone else will see something that is out of place. It this point I am out of ideas.  Sorry I could not figure this out for you.

One last thing to look at just to see if anything is out of the ordinary,  type this in the terminal and post it.

sudo fdisk -l   that is the letter l not the number 1.


Also type sudo cat /etc/fstab and post it.

---

### Post by joe0867 on 2009-07-07
G_man did you solve your issue?

---

### Post by joe0867 on 2009-07-07
I might be able to help

but require some info

---

### Post by G_man on 2009-07-07
I would appreciate your help. I did not solve it yet. What do you need to know?

---

### Post by lindsay7 on 2009-07-07
If you could post the outputs of the commands that I gave you. I just want to check the uuid's against the partition numbers.

---

### Post by G_man on 2009-07-07
(hd0,0)

---

### Post by lindsay7 on 2009-07-07
This is what I would like to check.

One last thing to look at just to see if anything is out of the ordinary, type this in the terminal and post it.

sudo fdisk -l that is the letter l not the number 1.


Also type sudo cat /etc/fstab and post it.

---

### Post by G_man on 2009-07-07
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbe80135

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18709   150280011   83  Linux
/dev/sda2           18710       19457     6008310    5  Extended
/dev/sda5           18710       19457     6008278+  82  Linux swap / Solaris


sudo cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

---

### Post by lindsay7 on 2009-07-07
Ok, Let first say that I know you installed Ksplice and I am not familiar with that application at all, so your file system may be the way it is because of that but, this does not look right at all based on the standard Ubuntu install. There is a lot of data on sda1 but there is no root or "/" partition. The whole thing looks strange and I can see why it will not boot.

Unless some has more information on what is going on here, I would say that you need to do a complete system re-install. Back up everything that you need first.

Give it some time before you do anything in case you get some other input. I am going to forward your post to Merlinus who is really good at looking at these things and see if he can give you some more help.

---

### Post by lindsay7 on 2009-07-07
Here is the way my file system looks, for example.

[ATTACH]120298[/ATTACH

---

### Post by merlinus on 2009-07-07
Post results of

```

sudo blkid
mount
df-h
```

---

### Post by G_man on 2009-07-07
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbe80135

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18709   150280011   83  Linux
/dev/sda2           18710       19457     6008310    5  Extended
/dev/sda5           18710       19457     6008278+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="dd89765a-440f-4852-8960-f5cc536a33b1" TYPE="ext3" 
/dev/sda5: UUID="d933defa-d75f-448f-b606-86f501c22bf8" TYPE="swap"

---

### Post by merlinus on 2009-07-07
What about 
```
mount
df -h
```

---

### Post by G_man on 2009-07-07
> **lindsay7 said:**
> Here is the way my file system looks, for example.

[ATTACH]120298[/ATTACH

I don't think there is a problem with the way my partitions are. You are using Windows in your NTFS partition and making it the primary partition. While I only have one OS and I don't think there is a problem with making ext3/4 a primary partition. Beside, it was always this way and never had a problem with it (Since March!)

I am getting desperate. I really don't want to format my pc :(

---

### Post by G_man on 2009-07-07
mount
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
/dev/sda1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)




ubuntu@ubuntu:/media/disk-1/home/aman/Downloads/android/Root/AndroidMod/SignApk$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1003M  2.0M 1001M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1003M  2.0M 1001M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  108K 1002M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M   92K 1003M   1% /dev
tmpfs                1003M   76K 1003M   1% /dev/shm
rootfs               1003M   95M  908M  10% /
/dev/sr0              698M  698M     0 100% /cdrom
/dev/loop0            674M  674M     0 100% /rofs
tmpfs                1003M  416K 1002M   1% /tmp
/dev/sda1             142G  121G   14G  91% /media/disk-1

---

### Post by merlinus on 2009-07-07
```
/dev/sda1             142G  121G   14G  91% /media/disk-1
```Is ubuntu's root partition on some sort of removable device?  I ask because clearly sda1 is not mounted as /, but as media/disk-1.

This is almost certainly why you are experiencing problems with trying to reinstall grub.

Also, if you look at /etc/fstab, there is no mountpoint for sda1 as /.

And what is this:

aufs / aufs rw 0 0

---

### Post by lindsay7 on 2009-07-07
Merlinus,

I found this on aufs file systems. There is some info on editing the grub file in this.

[https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash)

---

### Post by merlinus on 2009-07-08
Very interesting, Lindsay, and also very interesting that support for aufs is not being built into 9.10 either.

FWIW, this system seems like a very difficult alternative to using a hdd for linux.  But I wonder why installing a KDE app broke grub for the OP...  Must be all those extra libraries, and that the aufs system seems difficult to write to directly, so maybe the install did something weird.

---

### Post by G_man on 2009-07-08
I am an android developer and have three emulators for that. I also use lots of virtual machines. I connect sdcards to the machine all the time. I am using liveCD. If I use an sdcard, The system goes /media/disk-1. If i don't the system goes /media/disk

The liveCD is mounted as /

---

### Post by lindsay7 on 2009-07-08
Merlin, thanks for looking at this. I had no idea this system was around and I surely do not understand what is going on here.


G-man, you may want to start a new thread and ask for help with restoring a aufs system. You may find someone who has experience with this system that way if the post points out your situation with it.  The Grub error title may not catch the attention that you need.

---

### Post by G_man on 2009-07-08
OK thanks very much but can you tell me what is this aufs system?

---

### Post by G_man on 2009-07-08
Anyway, thanks to both of you guys.

---

### Post by joe0867 on 2009-07-08
G_man still there?

Sorry I left yesterday.  Had to.

---

### Post by G_man on 2009-07-09
Yes, I am here. No problem.

Do you have any idea of how to solve this problem?

---

### Post by merlinus on 2009-07-09
[http://en.wikipedia.org/wiki/Aufs](http://en.wikipedia.org/wiki/Aufs)

---

### Post by tantos on 2009-08-14
hi G_Man, I have the same problem too.
I try [http://www.unix.com/ubuntu/105766-grub-loader-2.html](http://www.unix.com/ubuntu/105766-grub-loader-2.html), and now it's solved

---

### Post by Zalbor on 2009-08-18
> **merlinus said:**
> ```
/dev/sda1             142G  121G   14G  91% /media/disk-1
```Is ubuntu's root partition on some sort of removable device?  I ask because clearly sda1 is not mounted as /, but as media/disk-1.

This is almost certainly why you are experiencing problems with trying to reinstall grub.

Also, if you look at /etc/fstab, there is no mountpoint for sda1 as /.

And what is this:

aufs / aufs rw 0 0
I might be way off the record here, but maybe G_man is posting the fstab of the live CD, instead of the installed system's? That would have sda1 somewhere in /media...

On the original issue: It still might be nothing (I'm far from perfect on my grub knowledge) but your menu.lst seems to have "root" commands with UUID strings, instead of device strings (like "(hd0,0)"). On my system, those lines begin with "uuid" instead of "root"...

---

### Post by Taemojitsu on 2009-10-02
Zalbor, yes that's it. For anyone who finds this thread: grub seems to require the (hdx,y) format with the 'root' command. The word 'uuid' does not even appear in the gnu grub manual at all, it might be added by someone else such as Ubuntu to make grub more useful. Maybe grub2 allows a disk uuid to be used with the 'root' command, I'm pretty sure how mine got messed up was trying to use grub2 to detect a windows partition and regenerating menu.list. But if you encounter **grub error 11** and can't figure out what's wrong check the keywords. ;/ The other tip is when the menu titles change inexplicably, since it probably means some other distribution or script tried to update menu.list, and kept the identifier despite changing the keyword in an attempt to be more compliant with the GNU standard, there's probably multiple versions of grub for different distributions treating these keywords differently.

---

