---
title: "Adding Fedora to grub"
date: 2009-09-14
forum: General Help
---

### Post by Muscovy on 2009-09-14
I recently installed Fedora. I'm trying to make Ubuntu's grub point "Fedora 11" to Fedora's grub. However, everything is failing and giving errors.
  Here's the details:
sda5 - Ubuntu.
sda8 - Fedora main.
sda7 - Fedora's /boot. I don't know why it's a partition.

Thanks.

---

### Post by quixote on 2009-09-16
To have some idea of what the problem might be, it would help to see the relevant part of menu.lst, the bit toward the end that lists the various boot options you have.

Also, what sorts of error messages are you getting?

(There's a lot of information here that might help: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) )

---

### Post by Muscovy on 2009-09-16
I removed Fedora yesterday, because I realised when I looked at the ISO I'd gotten Gnome, when I wanted to give KDE a go. I'll try again, of course.
  The issue was that Fedora didn't add itself to Grub, it just asked if I wanted no Grub or replace existing. I did deal with the partitions manually, so maybe that's why I missed out on an autoprepare. I've never added an OS after installing Ubuntu, so maybe I just totally am missing something basic. I'll take a look at that link.



Edit: It sounds like I needed to do additional setup to point to the /boot partition of Fedora. In future, do I need a *partition* for /boot?

---

### Post by quixote on 2009-09-17
You don't have to have a separate partition for boot.  (Certainly not for ubuntu.  The last time I used Fedora was 3, but then fedora didn't require it either.)  Some people do it that way because it means you can upgrade parts of the system without changing anything else, such as other programs you've installed.  

I've found it more useful to have separate / and /home partitions.  That means I have to reinstall programs if I do a clean install (which with the amount of kruft I accumulate is a good idea anyway), but all my settings and data stay just as they are.

---

### Post by Muscovy on 2009-09-19
The home folder separate sounds like a really good idea. I like dabbling in multiple OSs, and it'd be very nice to have a centralized document location.

---

### Post by Muscovy on 2009-09-20
I can't find a way to let grub point to another partition, for anything other than Windows. I gave OpenSolaris a go, and this failed:

title	OpenSolaris
root	(hd0,3)
chainloader	+1
makeactive
boot

---

### Post by oldfred on 2009-09-21
Grub is installed to the MBR of the first drive to boot. It will point to a menu.lst to allow you to choose other operating system or to chainboot to a copy of Grub installed in a partition that allows you to choose the versions of the system in that partition.

Does Opensolaris install a grub/boot entry in the partition? If so you can chainboot from your ubuntu MBR/menu.lst to that partition with :

title OpenSolaris 
root (hd[COLOR=Red]x[/COLOR],[COLOR=Red]y[/COLOR])
chainloader +1

Where x,y is your opensolaris partition like (hd0,3) for sda4.

---

### Post by Muscovy on 2009-09-21
That was my intention, to have the OpenSolaris entry point to the OpenSolaris grub.
  So what's wrong with the config I posted? I'll give it a go without the makeactive and boot.


Edit: ...ooookay. When I select OpenSolaris it says "GRUB: " for about 5 seconds, then goes back to the main grub.

---

### Post by oldfred on 2009-09-21
It does not sound like you have grub in the opensolaris partition? Is it a primary partition? Are you pointing to the correct partition? To help answer all these type of questions let's fully document you configuration by running a script:
Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
creates results.txt in the same directory, post with code tags as it will be long.

I also suggest if you are using multiple distributions you should have all your data - documents, pictures, movies etc. in a separate /data partition to share between distributions. /home can be mounted but should not be the same user in /home or same /home as different versions of software may have slightly different config files. A separate /home is great for when you do a clean reinstall of your distribution as then you have all your data saved without separate backup.

---

### Post by akudewan on 2009-09-21
> **Muscovy said:**
> The home folder separate sounds like a really good idea. I like dabbling in multiple OSs, and it'd be very nice to have a centralized document location.

Offtopic, but since you mentioned it:
Sharing /home between multiple linux distros may cause problems. The hidden config files (.gconf/, for instance) from one distro may be overwritten by another. If the sofware versions don't match, there will be more trouble.

You could share a separate 'Documents' partition between both distros and keep small, individual /home partitions. That should be safer IMO.

---

### Post by Muscovy on 2009-09-21
Here we go. I've bolded the section that looks important.
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 401790332 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

[B]sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda4 and looks 
                       at sector 471764840 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   
[/B]
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x55785733

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   174,288,895   174,082,048   7 HPFS/NTFS
/dev/sda3         174,289,185   471,764,789   297,475,605   5 Extended
/dev/sda5         318,424,428   465,435,179   147,010,752  83 Linux
/dev/sda6         465,435,243   471,764,789     6,329,547  82 Linux swap / Solaris
/dev/sda4         471,764,790   488,392,064    16,627,275  bf Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="B490D97D90D94710" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="546AE9EC6AE9CAB6" TYPE="ntfs" 
/dev/sda4: UUID="a5fec0b0-6a64-4942-a2a3-f6f2beef5fbb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="a9c1ec33-4050-4f3d-b617-1c915040ce37" TYPE="ext3" 
/dev/sda6: UUID="1e5b014a-830f-407d-a6ec-decedbe2fc25" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alex/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alex)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=a9c1ec33-4050-4f3d-b617-1c915040ce37 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a9c1ec33-4050-4f3d-b617-1c915040ce37

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		a9c1ec33-4050-4f3d-b617-1c915040ce37
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=a9c1ec33-4050-4f3d-b617-1c915040ce37 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		a9c1ec33-4050-4f3d-b617-1c915040ce37
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=a9c1ec33-4050-4f3d-b617-1c915040ce37 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		a9c1ec33-4050-4f3d-b617-1c915040ce37
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a9c1ec33-4050-4f3d-b617-1c915040ce37 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a9c1ec33-4050-4f3d-b617-1c915040ce37
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a9c1ec33-4050-4f3d-b617-1c915040ce37 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a9c1ec33-4050-4f3d-b617-1c915040ce37
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title	OpenSolaris
root	(hd0,3)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Garry's Mod
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=a9c1ec33-4050-4f3d-b617-1c915040ce37 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1e5b014a-830f-407d-a6ec-decedbe2fc25 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

=================== sda5: Location of files loaded by Grub: ===================


 205.7GB: boot/grub/menu.lst
 205.7GB: boot/grub/stage2
 205.7GB: boot/initrd.img-2.6.28-11-generic
 205.8GB: boot/initrd.img-2.6.28-15-generic
 205.7GB: boot/vmlinuz-2.6.28-11-generic
 205.8GB: boot/vmlinuz-2.6.28-15-generic
 205.8GB: initrd.img
 205.7GB: initrd.img.old
 205.8GB: vmlinuz
 205.7GB: vmlinuz.old

```

---

### Post by oldfred on 2009-09-21
I went back and looked at the script and it looks like it will not find the Solaris operating system to show it, so it is probably still there. The script is designed for standard linux and windows. The script did show you have grub in sda4. Your boot should work, here is an example of someone doing exactly the same thing:
[http://forums.amd.com/devblog/blogpost.cfm?threadid=114137&catid=209](http://forums.amd.com/devblog/blogpost.cfm?threadid=114137&catid=209)

---

### Post by quixote on 2009-09-21
What I know about OpenSolaris could fit on a postage stamp, and I'm sure others here will have a better answer for you.  OpenSolaris has a jillion idiosyncracies.  I would guess that the problem is that it keeps the boot files in some weird directory (/rpool/boot ??) which is not grub's default.  Since you haven't specified where on (hd0,3) grub is to look for the files it needs, it's looking in the wrong place.

So, anyway, long way to say I don't know the answer, but I suspect that all you need is the proper locations for your OpenSolaris boot files specified in that menu.lst.

---

### Post by Cubby on 2009-09-22
> **Muscovy said:**
> I recently installed Fedora. I'm trying to make Ubuntu's grub point "Fedora 11" to Fedora's grub. However, everything is failing and giving errors.
  Here's the details:
sda5 - Ubuntu.
sda8 - Fedora main.
sda7 - Fedora's /boot. I don't know why it's a partition.

Thanks.

Did you install the live version of Fedora 11?  I just did, and found out after the fact (no help menu during install process) that you have to install the live version by creating two partitions, one for /boot which can be ext2 or ext3, and one for /  as ext4. Apparently, this was a bug that was too late to fix as it was already released.  The fedora devs are saying this won't be a problem with version 12's live disc.  Hmmm.  Maybe this is the reason you are having problems.  I am having problems, too, as this partition set up isn't allowing me to have my other two linux distros show up in the fedora grub menu, only xp shows up.

Edited to add, that I got Fedora 11 live KDE to show up in my particular Linux distro, finally!.  My first hard drive: 
xp ntfs on /dev/sda1
ntfs partition on /dev/sda2
main linux distro a /dev/sd5
On my second hard drive:
linux distro b /dev/sd1
fedora's /boot partition /dev/sdb2
fedora-11-x86_64 /dev/sdb3

To find the relevant information for Fedora, I booted into my other favoured distro,  I then opened up terminal, switched to root, then 
cat /mnt/sdb2/grub/menu.lst 
and copied the entry for Fedora into my preferred boot menu, saved file.  sdb2 is the volume where Fedora's grub info. is, such as vmlinuz, initrd, system map, and grub is located.  You should be able to find yours by looking over the entries in your file manager, which you have two for Fedora.  Look for the one with the the files I listed above.

---

### Post by Darkwing-Duck on 2009-09-23
Try refreshing the menu.list this way.

[http://gwos.org/udsf/doku.php/core:grub:restore#adding_other_installs](http://gwos.org/udsf/doku.php/core:grub:restore#adding_other_installs)

---

### Post by Muscovy on 2009-10-03
I went back to trying to get Fedora going. I tested putting Ubuntu, then Fedora on a VM disc, and updated Ubuntu's grub to have Fedora. This was with Fedora 11, and it worked. I did the same thing on my real drive, and it... didn't.
  I tracked it down as far as my real Fedora /boot being unviewable, at least from Ubuntu. I have no idea what's going on.

---

