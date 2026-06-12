---
title: "deleted kernels &amp; grub problem"
date: 2010-08-01
forum: General Help
---

### Post by fh37 on 2010-08-01
Hi,

I'm new to Linux so please bear with me. I am running ubuntu 10.04  and XP on my laptop (dual-boot). I had an original problem, spent a week  searching for solutions and trying new things, and ended up with a  second issue without resolving my first one.
   
Original problem:
I attempted to clean up my boot menu using  these instructions: [http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/).  I was supposed to use synaptic to remove old kernels, but accidentally  deleted all my kernels with the exception of  2.6..28.15-generic. When I selected this kernel option from the boot menu, I got to my login screen, but it froze there. 

I thought I could solve this problem by booting using a live CD, mounting the linux partition and copying   the kernel files from the live CD to the linux partition. However, I kept getting  errors while trying to copy the files.

Subsequent problem:
While in the process of trying things that would hopefully work, I reinstalled GRUB from my live CD -- I erroneously tried to adapt instructions used to solve a similar problem. After booting from a Live CD, mounting the linux partition and reinstalling GRUB, I the boot menu that allowed me to dual-boot. Instead, I only have a very basic grub command line when I turn on my laptop.

So at this point I figured I should get some advice before potentially screwing up things further. 

I am hoping to receive help to:
a) get back my Grub boot menu
b) reinstall my kernel so I can successfully boot ubuntu 10.04

This is my first post on here so I apologize if it's in the wrong place or I haven't followed correct etiquette. Please let me know if you need any other information (from reading other threads it seemed like posting my boot info script  could be useful). Thank you for your help.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,594,960   211,912,703   199,317,744   7 HPFS/NTFS
/dev/sda3         211,913,415   215,913,599     4,000,185  82 Linux swap / Solaris
/dev/sda4         215,913,600   312,576,704    96,663,105  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4005 MB, 4005527552 bytes
32 heads, 63 sectors/track, 3880 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,822,079     7,822,017   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AC9472FB9472C6FC                       ntfs       RECOVERY                      
/dev/sda2        E02874A2287478FC                       ntfs                                     
/dev/sda3        d962bdd8-b2fe-450b-9abb-df0762ab8537   swap                                     
/dev/sda4        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C09E-D1A3                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda4        /media/93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7

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

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic
uuid        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Chainload into GRUB 2
root        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7
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
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
chainloader    +1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=d962bdd8-b2fe-450b-9abb-df0762ab8537 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 110.6GB: boot/grub/core.img
 111.7GB: boot/grub/menu.lst
 112.3GB: boot/grub/stage2
 110.6GB: boot/initrd.img-2.6.28-15-generic
 143.6GB: boot/vmlinuz-2.6.28-15-generic
```

---

### Post by fh37 on 2010-08-03
Anyone have thoughts on this? Thanks.

---

### Post by Cavsfan on 2010-08-03
I cannot help that much on your problem, but if you post a link to this post in this thread I am sure you will get some answers
[[COLOR=blue]_ This GRUB2 Help thread._[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

And when you get it all sorted out, take a look in my signature on how to fix your GRUB2 menu to where it is maintenance free.
No need to change/update it every time a kernel comes in.

Also I would suggest using Ubuntu Tweak for getting rid of old kernels. It does it safely.

I did exactly what you did - removed my good kernel and didn't really want to ask a bunch of questions, so I did a clean install.

But, I am sure you can recover w/o a clean install.
Just post in the thread I mentioned and **Drs305** will hook you up!

---

### Post by fh37 on 2010-08-03
Thanks Cavsfan! Yeah, I'm hoping to recover w/o a clean install. 

Your tutorial looks great. I'll be sure to use it once I'm up and running again.

---

### Post by Cavsfan on 2010-08-03
> **fh37 said:**
> Thanks Cavsfan! Yeah, I'm hoping to recover w/o a clean install. 

Your tutorial looks great. I'll be sure to use it once I'm up and running again.

Thank you!
It will be great for you since you dual boot windows too. 

Just remember to put your custom entries in **/etc/grub.d/40_custom**, but make sure you save that file as **/etc/grub.d/06_custom.**
And leave 04_custom as it was.
That way the custom entries will appear first.

---

### Post by drs305 on 2010-08-03
fh37,

You have an interesting dilemma. From your post, it appears you are running Lucid, so I will use that assumption. I suspect you aren't having success booting because of the kernel you have on your computer, which goes back to Jaunty. I'd normally recommend a clean install, but since you said you wanted to try to avoid that, here is something you can try. No guarantees though.

I think we can get the current kernel reinstalled via chroot. I'm not a chroot expert, but we'll see if we can do it and then try to get Grub2 installed on your system.

You will need to boot the Lucid LiveCD to the Desktop. Once there, open a terminal and run this series of commands to 'chroot' into your real Ubuntu install:

```

sudo mount /dev/sda4 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys  && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

```
This should take you to a root prompt, and all the commands you now run from the LiveCD will impact your real Ubuntu install. The use  of "sudo" and "gksu" are not required in the chroot environment.

Attempt to install the latest Lucid kernel:
```
apt-get install linux-image
```
If that is successful, check the contents of /boot. You should see a linux kernel (vmlinuz-2.6.32-24-generic or equivalent) and an initrd.img (
vmlinuz-2.6.32-24-generic or equivalent).

If that worked, exit the chroot with "exit". At the normal prompt, run this command to unmount what you previously mounted:
```

sudo umount /mnt/dev/pts /mnt/proc /mnt/sys /mnt/dev /mnt

```

Now, to install Grub2. It may have been easier to stick with chroot, but this is a tested way of installing Grub2. 

You can get Grub2 installed on your system with the following:

First you will mount your real Ubuntu partition (/dev/sda4) on /mnt. Next you will install the Grub2 files to the MBR (sda) and Ubuntu partition (sda4). Note that you do not install Grub2 to the partition in the second command.

```
sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Remove the CD after running these commands and reboot. 

You will now have the Grub2 menu. If you don't see it displayed, hold down the SHIFT key during the early stages of the boot process and it should show up.

Also, if you can boot but don't see the Windows OS, run "sudo update-grub" once again to allow Grub2 to find Windows.

---

### Post by fh37 on 2010-08-03
drs305, thanks for the instructions.

I was able to 'chroot' properly, but was unable to install the latest Lucid kernel. Here is the message I got:
```
root@ubuntu:/# apt-get install linux-image
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-headers-2.6.34-020634-generic: Depends: linux-headers-2.6.34-020634 but it is not installable
  linux-image: Depends: linux-image-generic (= 2.6.32.22.23) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```I double-checked the /boot folder on the correct partition and the files are not there. Let me know what you think. 

Thanks!

---

### Post by drs305 on 2010-08-04
Did you try running the command suggested in the error message? (apt-get -f install)

I didn't know if you could use this method to reinstall the kernels or not. You might try installing a specific kernel rather than "linux-image". To do this, you could type "apt-get install linux-image-2.6.3" and then double-TAB to see the available kernels. Then continue by typing a bit more from the list of the available kernels and double-TAB again to autocomplete the entry.

I would think if it won't accept "linux-image" it probably wouldn't work via this method either, but it might.

If you don't have data or many customizations on the Ubuntu drive, it is often faster to reinstall than continue to try to troubleshoot a system. It depends on how quickly you need to get your system back and how much effort you have 'invested' in your current installation.

---

### Post by fh37 on 2010-08-05
Thanks drs305. So I think I'm almost there. 

After running 'apt-get -f install' and then 'apt-get install linux-image,' I checked the /boot folder and the new kernel files are there.

In case you are curious here is the output from those commands:
```
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
 firefox-3.5-branding libqt4-assistant kakasi-dic libgfortran3 libqt4-test
 python-sqlalchemy kakasi ttf-lyx libqt4-xmlpatterns libqt4-help python-qt4
 python-numpy blt python-tk libqt4-webkit python-tz python-sip
 python-matplotlib-data python-pysqlite2 libqt4-svg python-dateutil
 libphonon4 libblas3gf tcl8.5 python-pyparsing liblapack3gf tk8.5
 python-matplotlib libqt4-scripttools
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
 linux-headers-2.6.34-020634-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 11.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128461 files and directories currently installed.)
Removing linux-headers-2.6.34-020634-generic ...
root@ubuntu:/# apt-get install linux-image
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
 firefox-3.5-branding libqt4-assistant kakasi-dic libgfortran3 libqt4-test
 python-sqlalchemy kakasi ttf-lyx libqt4-xmlpatterns libqt4-help python-qt4
 python-numpy blt python-tk libqt4-webkit python-tz python-sip
 python-matplotlib-data python-pysqlite2 libqt4-svg python-dateutil
 libphonon4 libblas3gf tcl8.5 python-pyparsing liblapack3gf tk8.5
 python-matplotlib libqt4-scripttools
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
 linux-image-2.6.32-22-generic linux-image-generic
Suggested packages:
 fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
 linux-image linux-image-2.6.32-22-generic linux-image-generic
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.9MB/30.9MB of archives.
After this operation, 97.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main
linux-image-2.6.32-22-generic 2.6.32-22.36 [30.9MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main
linux-image 2.6.32.22.23 [3,946B]
Fetched 30.9MB in 4min 9s (124kB/s)
Selecting previously deselected package linux-image-2.6.32-22-generic.
(Reading database ... 121748 files and directories currently installed.)
Unpacking linux-image-2.6.32-22-generic (from
.../linux-image-2.6.32-22-generic_2.6.32-22.36_i386.deb) ...
Done.


Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from
.../linux-image-generic_2.6.32.22.23_i386.deb) ...
Selecting previously deselected package linux-image.
Unpacking linux-image (from .../linux-image_2.6.32.22.23_i386.deb) ...
Setting up linux-image-2.6.32-22-generic (2.6.32-22.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-22-generic
/boot/vmlinuz-2.6.32-22-generic

Setting up linux-image-generic (2.6.32.22.23) ...
Setting up linux-image (2.6.32.22.23) ...
root@ubuntu:/#
```

However, I am still having a problem with Grub2. I ran the commands to mount my real Ubuntu partition and install the Grub2 files (sudo mount /dev/sda4 /mnt, then, sudo grub-install --root-directory=/mnt /dev/sda). No errors. 

But, when I boot I get this: 
```
GNU GRUB version 1.98-1ubuntu5

Minimal BASH-like line editing is supported. for the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>_
```

I tried holding down the shift key, but that only gave me a quick "grub loading" message and I got the same screen. I found a thread you had responded to that may be helpful (same boot problem): [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9509832]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9509832") 

And here are the updated results of my boot info script:
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,594,960   211,912,703   199,317,744   7 HPFS/NTFS
/dev/sda3         211,913,415   215,913,599     4,000,185  82 Linux swap / Solaris
/dev/sda4         215,913,600   312,576,704    96,663,105  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4005 MB, 4005527552 bytes
32 heads, 63 sectors/track, 3880 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,822,079     7,822,017   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AC9472FB9472C6FC                       ntfs       RECOVERY                      
/dev/sda2        E02874A2287478FC                       ntfs                                     
/dev/sda3        d962bdd8-b2fe-450b-9abb-df0762ab8537   swap                                     
/dev/sda4        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C09E-D1A3                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7 ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic
uuid        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Chainload into GRUB 2
root        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7
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
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
chainloader    +1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=93296a3e-b7a0-4fde-8a60-b3fc6b5ff3b7 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=d962bdd8-b2fe-450b-9abb-df0762ab8537 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 110.6GB: boot/grub/core.img
 111.6GB: boot/grub/menu.lst
 112.3GB: boot/grub/stage2
 110.6GB: boot/initrd.img-2.6.28-15-generic
 130.7GB: boot/initrd.img-2.6.32-22-generic
 143.6GB: boot/vmlinuz-2.6.28-15-generic
 114.7GB: boot/vmlinuz-2.6.32-22-generic
 130.7GB: initrd.img
 114.7GB: vmlinuz
```

Thanks again.

---

### Post by drs305 on 2010-08-06
It looks like your system is still trying to boot grub legacy (and apparently failing).

I have forgotten most of what I knew about grub legacy. You could try the following using the "chroot' method once again and completely remove grub and reinstall grub-pc.

Note: I have not tried this but it should work. 
From a chroot environment, if you would like to try it rather than reinstall, mount sda4 and chroot as previously, then run the following commands from inside the Lucid LiveCD 'chroot' terminal. MAKE SURE YOU HAVE AN INTERNET CONNECTION AND CAN DOWNLOAD IN CHROOT FIRST. You could try installing a small package such as 2vcard (apt-get install 2vcard).

The reason to test is that you will be removing grub for a very short period and all the boot files. You want to be able to reinstall them!

Here are the commands:
```
apt-get purge grub-common
apt-get install grub-pc
```
The first command should remove grub and grub-common.
The second command should install grub-common and grub-pc.

---

### Post by fh37 on 2010-08-06
Thank you drs305!

After successfully installing the small package you suggested, I was able to completely remove grub and reinstall grub-pc.

---

### Post by Cavsfan on 2010-08-07
> **fh37 said:**
> Thank you drs305!

After successfully installing the small package you suggested, I was able to completely remove grub and reinstall grub-pc.

Glad **drs205** was able to help you get it back w/o loosing everything! :)

Now, you can use some of **drs305**'s tutorials about GRUB2 and maybe my tut. on making GRUB2 maintenance free in my signature.
His has everything you'll ever want to know about GRUB2 and he is the one to see if you ever have a problem.
You shouldn't though. Once you got that fixed, you should be good to go. Lucid doesn't fall apart every other day! 
It is better than windows 7 in many ways IMHO.

Glad to see another happy Ubuntu'er :D

---

### Post by sineau on 2010-09-30
> **drs305 said:**
> fh37,

You have an interesting dilemma. From your post, it appears you are running Lucid, so I will use that assumption. I suspect you aren't having success booting because of the kernel you have on your computer, which goes back to Jaunty. I'd normally recommend a clean install, but since you said you wanted to try to avoid that, here is something you can try. No guarantees though.

I think we can get the current kernel reinstalled via chroot. I'm not a chroot expert, but we'll see if we can do it and then try to get Grub2 installed on your system.

You will need to boot the Lucid LiveCD to the Desktop. Once there, open a terminal and run this series of commands to 'chroot' into your real Ubuntu install:

```

sudo mount /dev/sda4 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys  && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

```
This should take you to a root prompt, and all the commands you now run from the LiveCD will impact your real Ubuntu install. The use  of "sudo" and "gksu" are not required in the chroot environment.

Attempt to install the latest Lucid kernel:
```
apt-get install linux-image
```
If that is successful, check the contents of /boot. You should see a linux kernel (vmlinuz-2.6.32-24-generic or equivalent) and an initrd.img (
vmlinuz-2.6.32-24-generic or equivalent).

If that worked, exit the chroot with "exit". At the normal prompt, run this command to unmount what you previously mounted:
```

sudo umount /mnt/dev/pts /mnt/proc /mnt/sys /mnt/dev /mnt

```

Now, to install Grub2. It may have been easier to stick with chroot, but this is a tested way of installing Grub2. 

You can get Grub2 installed on your system with the following:

First you will mount your real Ubuntu partition (/dev/sda4) on /mnt. Next you will install the Grub2 files to the MBR (sda) and Ubuntu partition (sda4). Note that you do not install Grub2 to the partition in the second command.

```
sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Remove the CD after running these commands and reboot. 

You will now have the Grub2 menu. If you don't see it displayed, hold down the SHIFT key during the early stages of the boot process and it should show up.

Also, if you can boot but don't see the Windows OS, run "sudo update-grub" once again to allow Grub2 to find Windows.
Thanks alot drs305. I deleted my linux image in a really foolish way, and following your guide it's now back. Just have to restart and make sure it works.

---

