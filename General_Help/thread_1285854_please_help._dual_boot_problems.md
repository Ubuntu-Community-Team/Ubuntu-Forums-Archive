---
title: "please help. dual boot problems"
date: 2009-10-08
forum: General Help
---

### Post by jollins69 on 2009-10-08
Hi as you can see im new here and im also new to linux. I have installed ubuntu 9.04 as part of my university course and unfortunately while installing the OS it has stopped my Windows 7 OS from loading. i know some of you might not like windows but i need both OS's working for my course and would appreciate if there is any information you have that could help me out.

I currently have ubuntu and windows 7 installed on my operating system.

Windows 7 loads up untill just before loggin in and then restarts. 

This happend strainght after the install of ubuntu.

i have tried the startup repair but no luck there (not that it ever works anyway).

thanks for reading. 

Jollins

---

### Post by zeroseven0183 on 2009-10-09
How did you install Ubuntu? Is it inside Windows?

---

### Post by akakingess on 2009-10-09
zeroseven0183 is correct, we need a little more info, for instance were you trying to set up a dual boot, or did you install it within Windows, etc. Any information that you can give us will help try to figure out the root of the problem.

---

### Post by PrePenguin on 2009-10-09
Also upon boot up if it shows two windows bootloaders listed choose the bottom windows bootload it will do a file system check and a checkdisk .. This is common on Vista and not sure on windows 7 after installing ubuntu.

---

### Post by jollins69 on 2009-10-09
hi thanks for the replies. 
I installed off of a live disk. I was trying to set up a dual boot with windows 7. It appears on the boot loader, the recovery partition and the OS but it wont load past the log on screen. It BSOD's. I am going to try a CHKDSK not and as it will take an hour or so il get back to you if it solves the problem.

---

### Post by jollins69 on 2009-10-09
just done the chkdsk. took over an hour :(

didn't fix the problem though. came up with a whole lot of errors or something. iv never seem it behave that way and iv done allot of chkdsks before.
still BSOD ing . getting desperate now cus my sound doesn't work on ubuntu either. this is turning into a nightmare...

any help would be appreciated

---

### Post by Gatemaze on 2009-10-09
When you were installing ubuntu did you manually partition your hard disk and installed it on a new "clean" partition or did you ask to automatically repartition the windows partition and then install it there?

---

### Post by jollins69 on 2009-10-09
> **Gatemaze said:**
> When you were installing ubuntu did you manually partition your hard disk and installed it on a new "clean" partition or did you ask to automatically repartition the windows partition and then install it there?

i created a new partition and installed on that. i had moved the recovery partition on the disk but this shouldn't of affected the OS though.

---

### Post by jollins69 on 2009-10-11
bump :)

---

### Post by louieb on 2009-10-11
> **jollins69 said:**
> i created a new partition and installed on that. i had moved the recovery partition on the disk but this shouldn't of affected the OS though.

What did you use to partition with?  If you moved the start of the Win 7 partition that can and probably did mess it up.  

Need a closer look.
Please download [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") - it creates file results.txt. Put its content in your next post.
to run
     

     ```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by jollins69 on 2009-10-11
> **louieb said:**
> What did you use to partition with?  If you moved the start of the Win 7 partition that can and probably did mess it up.  

Need a closer look.
Please download [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") - it creates file results.txt. Put its content in your next post.
to run
     

     ```
sudo bash ~/Desktop/boot_info_script*.sh
```

Cheers. i moved only the recovery partition. I created the partitions with paragon partition manager, kinda wish i hadn't. Was super slow and seemed a little glitchy. I did however resize the 7 partition to make room for ubuntu.

---

### Post by louieb on 2009-10-11
I still want the output from the script.  Anything I could suggest would be just a guess. With the output - it would be an educated guess.

If Ubuntu won't boot either then do it from the live CD.

---

### Post by jollins69 on 2009-10-11
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80d2f3ee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   544,137,614   544,137,552   7 HPFS/NTFS
/dev/sda2         544,137,615   563,016,078    18,878,464   7 HPFS/NTFS
/dev/sda3         563,030,055   621,233,549    58,203,495  83 Linux
/dev/sda4         621,233,550   625,137,344     3,903,795   5 Extended
/dev/sda5         621,233,613   625,137,344     3,903,732  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5C44C4595AB00B44" TYPE="ntfs" 
/dev/sda2: UUID="4064B29264B28A64" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="ae28c595-5f31-4dbf-94fb-2b6a210a969a" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="d7c9136a-18d5-4b92-93a7-c86a3aa01e77" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ae28c595-5f31-4dbf-94fb-2b6a210a969a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ae28c595-5f31-4dbf-94fb-2b6a210a969a

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        ae28c595-5f31-4dbf-94fb-2b6a210a969a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae28c595-5f31-4dbf-94fb-2b6a210a969a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        ae28c595-5f31-4dbf-94fb-2b6a210a969a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae28c595-5f31-4dbf-94fb-2b6a210a969a ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ae28c595-5f31-4dbf-94fb-2b6a210a969a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae28c595-5f31-4dbf-94fb-2b6a210a969a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ae28c595-5f31-4dbf-94fb-2b6a210a969a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae28c595-5f31-4dbf-94fb-2b6a210a969a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ae28c595-5f31-4dbf-94fb-2b6a210a969a
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


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=ae28c595-5f31-4dbf-94fb-2b6a210a969a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d7c9136a-18d5-4b92-93a7-c86a3aa01e77 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 296.1GB: boot/grub/menu.lst
 296.1GB: boot/grub/stage2
 296.1GB: boot/initrd.img-2.6.28-11-generic
 296.1GB: boot/initrd.img-2.6.28-15-generic
 296.1GB: boot/vmlinuz-2.6.28-11-generic
 296.1GB: boot/vmlinuz-2.6.28-15-generic
 296.1GB: initrd.img
 296.1GB: initrd.img.old
 296.1GB: vmlinuz
 296.1GB: vmlinuz.old

---

### Post by louieb on 2009-10-11
Don't know if good or bad news - after looking at the results.txt file don't see anything wrong. Looks like the 1st Win 7 (Vista) entry should work. - The 2nd is for a recovery boot. 

My Win 7 install boots from GRUB so I haven't looked closely at the recovery options on the Win 7 CD.  Have you tried its recovery console?  Thats all I know to do short of a reinstall.

---

### Post by jollins69 on 2009-10-11
> **louieb said:**
> Don't know if good or bad news - after looking at the results.txt file don't see anything wrong. Looks like the 1st Win 7 (Vista) entry should work. - The 2nd is for a recovery boot. 

My Win 7 install boots from GRUB so I haven't looked closely at the recovery options on the Win 7 CD.  Have you tried its recovery console?  Thats all I know to do short of a reinstall.

gah... seems like one problem after another tbh... bit sick of nothing working right. cant get my sound to work right either. working thru my headphone socket but not my speakers. not muted or anything... in fact it doesnt seem like my speakers are even picked up... 

well i guess im stuck then. unless anyone else has had this before and managed to fix it. does seem like a rather epic problem to solve.
 :(:(:( :'(

---

### Post by oldfred on 2009-10-11
Somewhere I saw a comment with Vista that with the makeactive command it would not work. Try removing that line and see it if makes any difference. As long as the partition is set as active it should not be required.

With speakers I have had the opposite problem. When every I install new drivers in Windows it loses my speakers. The work around was to unplug & replug in and then they worked. In linux they just work, the only issue in the past was often the default was muted or zero volume, but once I learned to set that up, no issues.

---

### Post by louieb on 2009-10-11
one last try. 
Try this recovery CD
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
and from Microsoft for Vista but should work for Win 7 too.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

and from the author of the Boot Info script. 
[How to fix XP when the boot files are missing - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=813628")

---

### Post by jollins69 on 2009-10-12
> **louieb said:**
> one last try. 
Try this recovery CD
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
and from Microsoft for Vista but should work for Win 7 too.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

and from the author of the Boot Info script. 
[How to fix XP when the boot files are missing - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=813628")

Thanks for the help. im gonna back up my documents at work today to make sure im safe before i go editing my OS cus i know what can happen. Il DL the disk there and if it works i can use it at work also. Countless people have come to us with vista and its completely smashed! :S

Got the Sound working BTW. Had to open the card configure thing and add some stuff. 

Well anyway its defo worth a try.

---

### Post by jollins69 on 2009-10-12
Still no luck. o well. i guess its game over for this little partition. Im just gonna back up all my data and then format the whole thing. shame though. 

thanks for your help guys.

---

### Post by screaminfakah on 2009-10-12
Try using the Super Grub Disk.  It can help you to restore your MBR, Grub boot loader, ect.
Just google it and you will find where to download it and how to use it.
Another idea is boot the Ubuntu live disc and look at the windows partiton to see if for some strange reason it is mounted.  If it is umount it and reboot.

---

