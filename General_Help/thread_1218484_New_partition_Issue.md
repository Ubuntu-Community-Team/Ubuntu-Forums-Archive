---
title: "New partition Issue"
date: 2009-07-20
forum: General Help
---

### Post by AustenB on 2009-07-20
Hi, I recently setup Ubuntu to dual boot with Vista, and used GParted to modify the existing partitions, and create a new one for data for Ubuntu. After partitioning everything, I've ran into two issues.

First, the new partition can only be accessed with sudo (i think that's what it's called) permission. I'd like to change this, considering it's just blank space and nothing valuable in it. I found this out because I can't copy anything onto the new drive cause it says I don't have the permission.

Second, and less important, my boot menu now lists everything twice. Before partitioning, It listed everything once. I'd like to fix this issue, but it's really not negatively effecting anything

Below is a copy of my menu.lst file, and attached is my GParted ss.

Help would be greatly appreciated :grin:

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ebc72e5e-2929-40d9-bc63-89b545e43967

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        ebc72e5e-2929-40d9-bc63-89b545e43967
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        ebc72e5e-2929-40d9-bc63-89b545e43967
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ebc72e5e-2929-40d9-bc63-89b545e43967
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ebc72e5e-2929-40d9-bc63-89b545e43967
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ebc72e5e-2929-40d9-bc63-89b545e43967
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

```

---

### Post by hibliss on 2009-07-20
The mount point on that Udata partition should be /home.

---

### Post by michy99 on 2009-07-20
> **hibliss said:**
> The mount point on that Udata partition should be /home.

I don't think he is using it as a /home partition, just a data partition. In that case, it can be mounted anywhere you want it.

AustenB, can you post the output to these commands?```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by AustenB on 2009-07-20
Okay, typing those commands in that order, I get:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x683fbc96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10490413+  27  Unknown
/dev/sda2   *        1307       14054   102397875    7  HPFS/NTFS
/dev/sda3           14055       22644    68999175    7  HPFS/NTFS
/dev/sda4           22645       30401    62308102+   5  Extended
/dev/sda5           22645       23919    10241406   83  Linux
/dev/sda6           30380       30401      176683+  82  Linux swap / Solaris
/dev/sda7           23920       30379    51889918+  83  Linux

Partition table entries are not in disk order

``````
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=95c0b81e-590a-4086-87f0-1fce1826097a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

``````
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/austen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=austen)
/dev/sda7 on /media/UDATA type ext2 (rw,nosuid,nodev,uhelper=hal)

```
And I tried changing the mount point, but gparted said it didn't kno where it should go, and I am using it just as a data drive so I think it's ok

---

### Post by michy99 on 2009-07-20
```
sudo umount /media/UDATA
sudo mkdir /media/UDATA
sudo chown $USER:users /media/UDATA
```Now open fstab for editing.```
gksudo gedit /etc/fstab
```Add this line:```
/dev/sda7 /media/UDATA  ext3    relatime        0       2
```Save the file and exit. Now see if it mounts.```
sudo mount -a
```If it works, it should auto-mount whenever you boot up.

---

### Post by AustenB on 2009-07-20
Well I did everything you said, but on the last step with "sudo mount -a" I get this error:
```
mount: wrong fs type, bad option, bad superblock on /dev/sda7,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by merlinus on 2009-07-20
Try ext2 instead of ext3.

```
/dev/sda7 /media/UDATA [COLOR=Red] ext2[/COLOR]    relatime        0       2
```

---

### Post by michy99 on 2009-07-20
My bad, I didn't catch that it is ext2. Hardly anyone uses it anymore.

---

### Post by merlinus on 2009-07-20
Since everything you told the OP to do was excellent advice, I took another, closer look at the gparted screenshot.

---

### Post by AustenB on 2009-07-20
Alright, thanks guys for the instruction, I changed it to ext2 and I didn't get an error message anymore.  I rebooted and everything boots up normal, just as it did before.

But, both my issues posted in my first post still exist.

So, not trying to sound ungrateful (I know what I did was helpful to my setup), but what exactly did doing all that stuff just do?

And is there a way to fix the issues in my first post?

---

### Post by michy99 on 2009-07-20
What is the output of```
ls -l /media
```

---

### Post by merlinus on 2009-07-20
You can delete this from /boot/grub/menu.lst, since vista is on sda2:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

for permissions changes:

```
gksudo nautilus
```navigate to to mountpoint, rightclick, properties, permissions.

The ubuntu entries are for two different kernels,  Best to leave them as is.

---

### Post by AustenB on 2009-07-20
Mitchy, this is the output.
```
total 8
lrwxrwxrwx 1 root root    6 2009-07-19 10:18 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-07-19 10:18 cdrom0
drwxr-xr-x 3 root root 4096 2009-07-19 15:02 UDATA
```

I'm gonna work on what merlin said now

---

### Post by michy99 on 2009-07-20
If that doesn't work, try ```
sudo chmod 777 /media/UDATA
```

---

### Post by AustenB on 2009-07-20
I edited menu.lst and took out the hd0, 0 entry for vista, and I went through nautilus and changed the owner in the permission tab of UDATA to Austen, my username.  

Just curious Mitchy, but does that command that you just gave give permission to all users on the computer to use UDATA?  

Also, I heard ext3 greatly reduces fragmentation; should i change UDATA to this type?

---

### Post by michy99 on 2009-07-20
Yes, if you chmod 777 that will give all users permission.

I would suggest changing to ext3. Since you don't have much data stored on it yet, I would just back it up to another partition, reformat it to ext3 and change the line in fstab back to ext3.

Some people would even suggest using ext4, but I have not made that switch yet myself.

---

### Post by AustenB on 2009-07-20
Alright thanks for the info, I'll switch it to ext3 now then :D

---

