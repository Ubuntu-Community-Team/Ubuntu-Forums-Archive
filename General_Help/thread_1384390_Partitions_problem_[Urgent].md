---
title: "Partitions problem [Urgent]"
date: 2010-01-18
forum: General Help
---

### Post by superstalker on 2010-01-18
Okay, I just resized a partition to make space for Windows.

Everything went fine, installed windows directly, lost my grub loader (as expected).

Tried to restore grub loader
I inserted the live-cd, checked G-Parted, all my partitions are gone!
Check Disk Utilities, everything is fine!

I can't open the my Ubuntu partition, although I can open my Multimedia Partition.

I don't care much for my ubuntu partition, it only has programs on it that I can reinstall, the thing I'm worried about is my 200gig multimedia drive that has everything on it.

Please help

---

### Post by J V on 2010-01-18
And this is why you NEVER install windows on anything but a blank system, and you ALWAYS back your stuff up, sorry, mabey you can hire a detective to recover the data but for 200 gigs thats a hefty price...

---

### Post by superstalker on 2010-01-18
Okay my Multimedia partition isn't gone! Only the partition that had Ubuntu!
The only way I can acces it is via a live CD. Is there a possibility to back up 33gig of data? (preferably 104gig). Using internet or somesort?

---

### Post by superstalker on 2010-01-18
I don't get it... I made a special partition for Windows... And now Ubuntu is gone... (according to Gparted) my partitions are gone (although Disk Utilities says the complete opposite). And now I'm just screwed up... Getting kicked in the back meanwhile...

---

### Post by audiomick on 2010-01-18
When you are booted to the live CD, what does
sudo fdisk -l
produce?

-that is a lower case L, not a figure one.

---

### Post by superstalker on 2010-01-18
```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x754defe1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       27985   224789481   83  Linux
/dev/sda2   *       27986       29304    10594867+   7  HPFS/NTFS
/dev/sda3           29305       38913    77184292+   5  Extended
/dev/sda4           38464       38913     3614593+  82  Linux swap / Solaris
/dev/sda5           29306       38463    73561603+  83  Linux

```

---

### Post by audiomick on 2010-01-18
Ok, I reckon the partition is still there. As you can see from the list, there are 2 Linux partitions, one at sda1 and one at sda5. Should there be more than that?

I think all you need to do is correct the grub configuration.

I am afraid you will have to wait for someone who knows a bit more about that than me. I would have to read for hours to sort it out...:(

What might help is to post to confirm: Can you boot into windows, but not into Ubuntu?

Go here:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
and post the RESULTS.TXT file that the described process generates back here. That will give us information about the exact state of your grub and your disks.

---

### Post by superstalker on 2010-01-18
Well that's the whole problem you see, although (allmost) all my partitions are fine, I doubt that the Ubuntu-disk isn't, all the commands from terminal are based on that partition.

When I type a command based on boot/grub

Terminal says, no such directory, because he can't read my ubuntu partition somehow.

---

### Post by audiomick on 2010-01-18
I expect that grub is looking in the wrong place for the system partition.
As I said, go to that link and go through it. It isn't that difficult, and doesn't take that long. The results should help someone help you to put things right.

---

### Post by superstalker on 2010-01-18
```
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...

Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda4 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop

```

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x754defe1

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   449,579,024   449,578,962  83 Linux
/dev/sda2    *    449,579,025   470,768,759    21,189,735   7 HPFS/NTFS
/dev/sda3         470,768,760   625,137,344   154,368,585   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5         470,784,888   617,908,094   147,123,207  83 Linux
/dev/sda4         617,908,158   625,137,344     7,229,187  82 Linux swap / Solaris

/dev/sda3 overlaps with /dev/sda4

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="Multimedia" UUID="e61636a6-a1c3-4128-9787-4090cf26cecd" TYPE="ext3" 
/dev/sda2: UUID="48AC2096AC208094" TYPE="ntfs" 
/dev/sda4: UUID="637c9b6d-6a4c-44f1-8a70-6abeb34d63fa" TYPE="swap" 
/dev/sda5: UUID="cef4b7ad-8599-40f2-b052-c2a29be25e1c" SEC_TYPE="ext2" TYPE="ext3" 

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/Multimedia type ext3 (rw,nosuid,nodev,uhelper=devkit)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=cef4b7ad-8599-40f2-b052-c2a29be25e1c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cef4b7ad-8599-40f2-b052-c2a29be25e1c

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

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        cef4b7ad-8599-40f2-b052-c2a29be25e1c
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=cef4b7ad-8599-40f2-b052-c2a29be25e1c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        cef4b7ad-8599-40f2-b052-c2a29be25e1c
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=cef4b7ad-8599-40f2-b052-c2a29be25e1c ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic
uuid        cef4b7ad-8599-40f2-b052-c2a29be25e1c
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=cef4b7ad-8599-40f2-b052-c2a29be25e1c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
uuid        cef4b7ad-8599-40f2-b052-c2a29be25e1c
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=cef4b7ad-8599-40f2-b052-c2a29be25e1c ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, memtest86+
uuid        cef4b7ad-8599-40f2-b052-c2a29be25e1c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST 
```

---

### Post by audiomick on 2010-01-18
Good man!

Ok, first of all, I am far from expert at analysing that stuff but:

Your linux system is in sda5. The partition in sda1 must be your media.

If looks like you had updated to 9.10 using the update manager, right? There are some files, for instance menu.lst, that belong to grub legacy there. If you had done a fresh install of 9.10, it should have been grub2.

I don't think your attempt to re-install grub was successful. If there is an intact grub anywhere, the first bit of the results.txt file reads something like
```
=> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive in partition #1 for /boot/grub.
```
or
```
=> Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive in partition #1 for /grub/stage2 and /grub/menu.lst.

```
yours only refers to windows in the MBR.

Given that, I would suggest trying to re-install grub again.

If you want to stick with grub legacy, read up on it here
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

if you want to go to grub2, look here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Does that help you at all?

edit:
I just noticed something I don't like the looks of:
> /dev/sda3 overlaps with /dev/sda4

I wouldn't have thought it was possible to do that, but apparently it is there. I have no idea what that has for consequences, but I doubt that it is a good thing

---

### Post by superstalker on 2010-01-18
Problem it can't read my sda5...

```
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

```

---

### Post by audiomick on 2010-01-18
did you see the edit at the end of my last post? That goes beyond my knowledge, but could well be the cause of all the trouble.

---

### Post by superstalker on 2010-01-18
Now I have, but it doesn't help, thanks anyway!

---

### Post by audiomick on 2010-01-18
This has got me thinking...

You know, I am sure, that sda5 is a logical partition inside the extended partition sda3. So the order of partitions on the disk isn't 1 2 3 4 5, it is 1 2 3(with 5 inside) 4.

Looking at the first thing you posted once again, I see that sda3 and sda4 end at the same block, as I have highlighted in red.
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       27985   224789481   83  Linux
/dev/sda2   *       27986       29304    10594867+   7  HPFS/NTFS
/dev/sda3           29305      [COLOR="Red"] 38913[/COLOR]    77184292+   5  Extended
/dev/sda4           [COLOR="SeaGreen"]38464[/COLOR]      [COLOR="Red"] 38913[/COLOR]     3614593+  82  Linux swap / Solaris
/dev/sda5           29306      [COLOR="Blue"] 38463[/COLOR]    73561603+  83  Linux
```
sda 3 needs to end where sda5 ends, in blue, before sda4 starts, in green.

How did you do your partitioning?

---

### Post by superstalker on 2010-01-19
I made 3 Partitions:
 
1st Multimedia
2nd Windows
3rd Ubuntu partition with swap partition -> So it is 1 partition made from 2 partitions.
 
Multimedia partition is located in /home of my original Ubuntu partition.

---

### Post by audiomick on 2010-01-19
> **superstalker said:**
> I made 3 Partitions:

I meant to ask what tool you used.;) Was it Gparted, or something else?

---

### Post by superstalker on 2010-01-19
I used Gparted. (Don't know what other partition managers there are.)

I resized my Ubuntu partition and moved it. After succesfully editing, I restarted, nothing seemed wrong.

I couldn't find the "any"  key to start up the windows install :P. So it booted up Ubuntu just fine... After closing installed Windows, and you know the rest.

---

### Post by superstalker on 2010-01-19
I don't want to go in any further tough, a buddy of mine has an external HD, currently backing up all my files, gonna insert killdisk after that, and do a completely fresh install.

---

### Post by audiomick on 2010-01-19
Ok, if you can do that, it might be the easiest way. Good luck with it.

Windows first, then Ubuntu, but you already know that.

Think about making a separate /home partition for your Ubuntu. Around 10 - 15 GB mounted at / for the system, and as big as you think you need for your home directory mounted at /home. Then you can just re-mount it if you have to or want to re-instal somewhere down the track.

---

### Post by superstalker on 2010-02-08
Newb question: I've setted a new partition for all my multimedia, in case something goes wrong with one of the two OS's. The only way to do that is to set my partition as NTFS. But ubuntu won't/can't set my partition as home. Why is that?

---

