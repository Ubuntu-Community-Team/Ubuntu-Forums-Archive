---
title: "can't mount root file system"
date: 2009-11-07
forum: General Help
---

### Post by ArrSea on 2009-11-07
Hope I can get some help on this.
I can't get my computer to boot up correctly, even in recovery mode.
It says:

/scripts/init-top/brltty: 19: grep: not found

and then a whole bunch more lines that says it's checking USB and eth0 for something and then this:

Alert! /dev/disk/by-uuid/1f9bf9ce-e769-4ca8-baef-78cc47f0c010 does not exist. Dropping to a shell! 

I am running Ubuntu 9.10 on an Acer Aspire 5535. Do I need to create a recovery CD or what?

Hopefully someone can help!

Thanks,

ArrSea

---

### Post by louieb on 2009-11-07
Need more information about your setup Please follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

### Post by ArrSea on 2009-11-08
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1e325cea

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   608,510,069   608,510,007  83 Linux
/dev/sda2         608,510,070   625,137,344    16,627,275   5 Extended
/dev/sda5         608,510,133   625,137,344    16,627,212  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1f9bf9ce-e769-4ca8-baef-78cc47f0c010" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="a9309076-97f8-4825-98a4-7531004aea97" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1f9bf9ce-e769-4ca8-baef-78cc47f0c010 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1f9bf9ce-e769-4ca8-baef-78cc47f0c010

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

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        1f9bf9ce-e769-4ca8-baef-78cc47f0c010
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=1f9bf9ce-e769-4ca8-baef-78cc47f0c010 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        1f9bf9ce-e769-4ca8-baef-78cc47f0c010
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=1f9bf9ce-e769-4ca8-baef-78cc47f0c010 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-9-rt
uuid        1f9bf9ce-e769-4ca8-baef-78cc47f0c010
kernel        /boot/vmlinuz-2.6.31-9-rt root=UUID=1f9bf9ce-e769-4ca8-baef-78cc47f0c010 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-9-rt
quiet

title        Ubuntu 9.10, kernel 2.6.31-9-rt (recovery mode)
uuid        1f9bf9ce-e769-4ca8-baef-78cc47f0c010
kernel        /boot/vmlinuz-2.6.31-9-rt root=UUID=1f9bf9ce-e769-4ca8-baef-78cc47f0c010 ro  single
initrd        /boot/initrd.img-2.6.31-9-rt

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        1f9bf9ce-e769-4ca8-baef-78cc47f0c010
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=1f9bf9ce-e769-4ca8-baef-78cc47f0c010 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        1f9bf9ce-e769-4ca8-baef-78cc47f0c010
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=1f9bf9ce-e769-4ca8-baef-78cc47f0c010 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        1f9bf9ce-e769-4ca8-baef-78cc47f0c010
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1f9bf9ce-e769-4ca8-baef-78cc47f0c010 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a9309076-97f8-4825-98a4-7531004aea97 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-16-generic
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-14-generic.bak
    .0GB: boot/initrd.img-2.6.31-9-rt
    .0GB: boot/vmlinuz-2.6.28-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-9-rt
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by louieb on 2009-11-08
Good/bad news is I don't see anything wrong. The message
> Alert! /dev/disk/by-uuid/[COLOR=Red]1f9bf9ce-e769-4ca8-baef-78cc47f0c010 [/COLOR]does not exist. Dropping to a shell! 
I did a search for the UUID - it shows up in all the right places. blkid output, UUID and root statements in menu.lst, and /etc/fstab. 

And the message
> /scripts/init-top/brltty: 19: grep: not foundSounds like fsck might fix. 
from the live CD Gparted can do it. (in right click menu)
or from command line
```
sudo e2fsck -f -y -v /dev/sda1
```Saw kernels for both Jaunty and Karmic. Was this the 1st boot after upgradeing from Jaunty to Karmic?

---

### Post by ArrSea on 2009-11-08
Yes, I upgraded from Jaunty to Karmic. No, this was not the first boot.
Maybe this will help:

I installed some updates that Update Manager said were necessary. I really don't remember what they were.

So I just need to run those commands? Great! I am comfortable (mostly) with the command line so that's fine.

I realized I forgot to thank you, so (late) Thank You!

-ArrSea

---

### Post by ArrSea on 2009-11-08
Ok, so I ran the e2fsck thing. It now says this:
[FONT=monospace]ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  439686 inodes used (2.31%)
    4500 non-contiguous files (1.0%)
     837 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 21380/374/0
 4787918 blocks used (6.29%)
       0 bad blocks
       1 large file

  340207 regular files
   35173 directories
      68 character device files
      26 block device files
       2 fifos
     615 links
   64180 symbolic links (52584 fast symbolic links)
      21 sockets
--------
  440292 files


What now?
[/FONT]

---

### Post by louieb on 2009-11-08
Your welcome - it would be nice if the thing booted.
> what now? are you getting the same error when you boot? 

I'm out of ideas. Don't see any reason for it not to boot. The results.txt looks fine. fsck output looks fine.

---

### Post by ArrSea on 2009-11-08
I've been running a Xubuntu LiveCD I made (Luckily!) last week to get online to this forum. I'll reboot, and see what happens!

Thanks for all the help!

-ArrSea

---

### Post by ArrSea on 2009-11-08
Well, I rebooted. And it gave me the same error message I got at the start of all this:

Loading, please wait... 1f9bf9ce-e769-4ca8-baef-78cc47f0c010
/scripts/init-top/brltty: 19: grep: not found

Gave up waiting for root device. Common problems:
       -Boot args (cat /proc/cdmline)
           -Check rootdelay= (did the system wait long enough?)
           -Check root= (did the system wait for the right device?)
       -Missing Modules (cat  /proc/modules; ls /dev)

Alert! /dev/disk/by-uuid/1f9bf9ce-e769-4ca8-baef-78cc47f0c010 does not exist. Dropping to a shell!


So I am back to where I started. Only now I have less time to fix this. (Not meaning to imply that it was a waste of time, just that now I only have about 18 hours til I have to have it fixed). 

Any help or direction towards how I should copy off data from the HDD when it won't boot up?

(A link to a thread would be great! But I'll also see whaI can find).

I appreciate you taking the time to help me,

Thanks!

-ArrSea

---

### Post by louieb on 2009-11-08
Not familiar with Xubuntu. I normally use [Puppy Linux]("http://www.puppylinux.com/")  or System Rescue when I need a live CD.  Can you browse the hard drive from the live CD?

Anyway heres one way. 

make a directory 
```
sudo mkdir /mnt/z
```

mount your hard drive install on the directory.

```
sudo mount -t ext3 /dev/sda1 /mnt/z
```

Now you should be able to use your file bowser. - navigate to /mnt/z and you should see the files and folders in your hard drive install. 

And you should be able to copy your files off.   What a pain.  

> Loading, please wait... 1f9bf9ce-e769-4ca8-baef-78cc47f0c010
/scripts/init-top/brltty: 19: grep: not found

Really odd message have - never seen a /scripts directory in any Linux install. While your browsing you might check to see if that file is there.

---

### Post by ArrSea on 2009-11-08
Got to run here, but I just tried what you said. It worked! Now I can copy off the files I need!

Thank you, thank you, thank you!

You have been a great help! 
Wow, what a relief to be able to see my old familiar files again!

-ArrSea

(Should I mark this thread as Solved now?)

---

### Post by ArrSea on 2009-11-08
Well, the scripts directory isn't there. Which makes me wonder... how this all got started.
I had installed some new programs, and run some updates. Guess I'll be more careful about what I install.

Thanks for all your help,

ArrSea

---

### Post by superdoper on 2009-11-26
I've had exactly the same problem after upgrading to 9.10 on the first and all subsequent reboots.    Using the older kernel: 2.6.28-16-generic, I can boot into the system, but on the new version 2.6.31-15-generic it fails.  I can't use the old kernel for much because it has a different problem (X takes up 100% of CPU), so I need to get this fixed.  I think it has something to do with loaded modules...

---

### Post by $p00ky on 2010-01-20
Same problem here:

```
boot error: /scripts/init-top/brltty: 19: grep not found
```

I'm running Ubuntu 9.10 x86_64.
It was working with the kernels up to 2.6.31-15-generic but from the 2.6.31-16-generic I have this "grep not found" error.

Fortunately, I still have the 2.6.31-15-generic which works fine so I still can use my computer.
But no matter if I re-install, completely remove and re-install, or reconfigure the kernels 31-16 to 31-18, I keep having the same error.

I tried **update-initramfs**:
```
update-initramfs: Cannot update. Override with -t option.
```
**dpkg-reconfigure linux-image-2.6.31-18-generic** did not work neither (same pb as it's calling update-initramfs).

Any clue?

---

### Post by $p00ky on 2010-02-01
can u change SOLVED to OPEN or split the topic?
I still have this problem...

---

