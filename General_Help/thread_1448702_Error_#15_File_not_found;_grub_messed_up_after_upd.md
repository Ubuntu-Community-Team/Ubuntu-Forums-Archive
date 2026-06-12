---
title: "Error #15: File not found; grub messed up after updating"
date: 2010-04-06
forum: General Help
---

### Post by whitewalls on 2010-04-06
Hi all,

Been trying to solve this using Google for a while.  Well, I recently did: sudo apt-get dist-upgrade.  Now, whenever I boot up I get "Error #15: File not found."

From what I've gathered, something is wrong with my menu.lst

I've tried several things to fix this, but I can't figure it out.  Any help?  Here's part of my menu.lst, not sure what else to say. Thanks!

```


#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,0)
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
# kopt=root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=729e592c-231c-4a75-9890-a903e1eb207e

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



```

---

### Post by oldfred on 2010-04-07
With 9.10 is it an upgrade with grub legacy or a new install with grub2? Error 15 is often where both grubs are installed and they get confused.


To see your entire setup:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by whitewalls on 2010-04-07
> **oldfred said:**
> With 9.10 is it an upgrade with grub legacy or a new install with grub2? Error 15 is often where both grubs are installed and they get confused.


To see your entire setup:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

I'm not sure about the grub legacy/grub2.  I already had 9.10, and then I did the dist-upgrade.  I hadn't heard of grub until I started getting this problem.  Here is my results.txt.  I am not sure what to highlight.  Below the results.txt is the part that I've been messing with.  It used to look just like all the other entries.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hdc: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63   114,222,149   114,222,087  83 Linux
/dev/hda2         114,222,150   117,210,239     2,988,090   5 Extended
/dev/hda5         114,222,213   117,210,239     2,988,027  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1        729e592c-231c-4a75-9890-a903e1eb207e   ext3                                     
/dev/hda5        73cf7e79-8f08-435e-81ae-5cb61693516a   swap                                     
/dev/hdc                                                iso9660    SLAX                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw,si=b2cc58,xino=/mnt/live/memory/.aufs.xino,nowarn_perm)
/dev/hdc         /mnt/hdc                 iso9660    (ro,noatime)
/dev/hda1        /mnt/hda1                ext3       (rw,noatime)


=========================== hda1/boot/grub/menu.lst: ===========================

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
# title        Ubuntu 7.10, kernel 2.6.31-20-generic
# root        (hd0,0)
# kernel    /vmlinuz root=/dev/hda2 ro quiet splash
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
# kopt=root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=729e592c-231c-4a75-9890-a903e1eb207e

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=729e592c-231c-4a75-9890-a903e1eb207e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=73cf7e79-8f08-435e-81ae-5cb61693516a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== hda1: Location of files loaded by Grub: ===================


  56.3GB: boot/grub/menu.lst
  56.4GB: boot/grub/stage2

==================== hdc: Location of files loaded by Grub: ====================


    .0GB: boot/initrd.gz
    .0GB: boot/vmlinuz
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file



```
```

This is the one I've been changing... not sure if that's helping or not.

title        Ubuntu 9.10, kernel 2.6.31-20-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet


```

---

### Post by oldfred on 2010-04-07
You still have grub legacy (0.97). Nothing stands out, but your drives are referred to as hda not sda. It had to be a couple of years ago that the drivers were combined and all drives now are referred to as sda? I think some other distributions still use the hda nomenclature.


UUIDs are preferred as they are less likely to change. If you delete or add partitions the sdx,y numbers can change. But if you make major changes or delete a swap that can even change a UUID.

This is not correct in your first boot stanza:
root=/dev/sdb1
it is sda1 but since your system is use hda maybe hda1?

---

### Post by whitewalls on 2010-04-07
> **oldfred said:**
> 
This is not correct in your first boot stanza:
root=/dev/sdb1
it is sda1 but since your system is use hda maybe hda1?

I have tried all sorts of different combinations for hd(0,#) and hda#, nothing seems to work.  I also tried altering it with the UUID settings, still nothing.

Any other suggestions? I'm not sure if it matters, but right now I'm using a KDE liveboot cd.  Here's the latest thing I've tried, with hd(0,0) and hda1:

```

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-20-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-20-generic root=/dev/hda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by oldfred on 2010-04-07
Part or most of your /boot is not shown in the results.txt. It should show the kernels in the /boot directory and they are not there. Can you confirm that they are missing by browsing from your livecD.

You may have to chroot into your system and do another full update.

---

### Post by oldfred on 2010-04-07
Ignore the comments that anything should be hda. I now see you used SLAX as your liveCD and that must still use hda nomenclature. Ubuntu will need sda style settings.

If boot files are missing:

Of course you must first know what partition you want to mount, in this example I'm using sda1, if you are still using SLAX I do not know if the mount needs to say hda1?:

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).

apt-get update
sudo apt-get update && sudo apt-get upgrade  #this updates everything
#apt-get install linux-image-generic 
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories

update-grub
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by whitewalls on 2010-04-09
> **oldfred said:**
> 
If boot files are missing:

Of course you must first know what partition you want to mount, in this example I'm using sda1, if you are still using SLAX I do not know if the mount needs to say hda1?:


I tried your suggestions... still no luck.  :/  Yes, I think my boot files are missing.  I'm still using the KDE livecd, and when I search my harddrive, there are no files in /boot/ except the memtest.

---

### Post by oldfred on 2010-04-09
I do not think I should have commented this line out:
#apt-get install linux-image-generic 

It may be worth trying again or someone else may know exactly what command line it takes to get all the boot files reinstalled.

---

### Post by whitewalls on 2010-04-10
> **oldfred said:**
> I do not think I should have commented this line out:
#apt-get install linux-image-generic 

It may be worth trying again or someone else may know exactly what command line it takes to get all the boot files reinstalled.

Still trying to figure out how to get the boot files reinstalled.  I tried the suggested lines, but no luck.  Does it matter that I'm trying them from a KDE livecd?  Ack.

---

### Post by oldfred on 2010-04-10
KDE is just the desktop graphical manager, the underlying files at the same.

---

### Post by whitewalls on 2010-04-20
Still can't get my system booted.  :/ 

I've been messing around with all sorts of stuff... no luck.  Any new pointers?

---

### Post by oldfred on 2010-04-21
These are the files you need to get back into /boot

    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.28-20-generic
    .0GB: vmlinuz-2.6.31-20-generic

If you can copy them from a liveCD, that may work if these are all that is missing. If version is different (not -20) then you will have to edit your grub.cfg or rerun the sudo update-grub to find the correct version.

Did the chroot and update not work? What messages did you get?

---

### Post by whitewalls on 2010-04-21
> **oldfred said:**
> These are the files you need to get back into /boot

    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.28-20-generic
    .0GB: vmlinuz-2.6.31-20-generic

If you can copy them from a liveCD, that may work if these are all that is missing. If version is different (not -20) then you will have to edit your grub.cfg or rerun the sudo update-grub to find the correct version.

Did the chroot and update not work? What messages did you get?

I have all of those files, and the menu.lst points correctly.  I can't figure out what's wrong.  I finally got the new vmlinuz and intrd.img with an update, but still no luck.  I've tried all sorts of different "root (hd0,0)" and "root=" combinations.  The chroot and update worked, I guess... just didn't seem to fix the problem.  I'm not really sure what should happen when I chroot something, though.

---

### Post by whitewalls on 2010-04-21
> **oldfred said:**
> 

Did the chroot and update not work? What messages did you get?


I'm sorry, nevermind, when I chroot I get "cannot run command '/bin/bash': no such file or directory."

---

### Post by whitewalls on 2010-04-21
Update, sorry for the few replies in a row, I just found my Ubuntu liveCD, so I'm using it now.  No problems when trying to chroot now.

After chrooting... when I run "sudo apt-get update" it stalls at "99% ... waiting for headers" and after a while I get a few errors... the last of which is "W: Failed to fetch [http://ppa.launchpad.net/ubunut-win/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubunut-win/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found"

When I run "apt-get install linux-image-generic" I get "E: Couldn't find package linux-image-generic"

Everything seems to update fine... menu.lst appears normal... :\

---

### Post by oldfred on 2010-04-21
when I run from my system ( with a sudo) it works but tells me I have the most current package.
apt-get install linux-image-generic

Lets rerun the boot info script to see if I can see something else missing. It may be something we cannot see is also missing? Possibly rather than just running the updates force the reinstall of key parts of the system? But lets check script first.

---

### Post by whitewalls on 2010-04-22
> **oldfred said:**
> when I run from my system ( with a sudo) it works but tells me I have the most current package.
apt-get install linux-image-generic

Lets rerun the boot info script to see if I can see something else missing. It may be something we cannot see is also missing? Possibly rather than just running the updates force the reinstall of key parts of the system? But lets check script first.

Here is my most recent results.txt:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 112836935 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

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

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   114,222,149   114,222,087  83 Linux
/dev/sda2         114,222,150   117,210,239     2,988,090   5 Extended
/dev/sda5         114,222,213   117,210,239     2,988,027  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        729e592c-231c-4a75-9890-a903e1eb207e   ext3                                     
/dev/sda5        73cf7e79-8f08-435e-81ae-5cb61693516a   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
# title        Ubuntu 7.10, kernel 2.6.31-20-generic
# root        (hd0,0)
# kernel    /vmlinuz root=/dev/hda1 ro quiet splash
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
# kopt=root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=729e592c-231c-4a75-9890-a903e1eb207e

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title        Ubuntu, kernel Default
root        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro quiet splash
initrd        /boot/initrd
savedefault
boot

title        Ubuntu, kernel Default (recovery mode)
root        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro single
initrd        /boot/initrd
boot

title        Ubuntu, kernel 2.6.15-55-386
root        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.15-55-386 root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro quiet splash
initrd        /boot/initrd.img-2.6.15-55-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-55-386 (recovery mode)
root        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/vmlinuz-2.6.15-55-386 root=UUID=729e592c-231c-4a75-9890-a903e1eb207e ro single
initrd        /boot/initrd.img-2.6.15-55-386
boot

title        Ubuntu, memtest86+
root        729e592c-231c-4a75-9890-a903e1eb207e
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "GNU/Linux, Linux 2.6.15-55-386" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.15-55-386 root=/dev/sda1 ro   
    initrd    /boot/initrd.img-2.6.15-55-386
}
menuentry "GNU/Linux, Linux 2.6.15-55-386 (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.15-55-386 root=/dev/hda1 ro single 
    initrd    /boot/initrd.img-2.6.15-55-386
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=729e592c-231c-4a75-9890-a903e1eb207e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=73cf7e79-8f08-435e-81ae-5cb61693516a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  57.7GB: boot/grub/grub.cfg
  57.8GB: boot/grub/menu.lst
  57.7GB: boot/grub/stage2
  57.4GB: boot/initrd
  56.4GB: boot/initrd.img-2.6.15-54-386
  56.4GB: boot/initrd.img-2.6.15-55-386
  57.4GB: boot/vmlinuz
  56.3GB: boot/vmlinuz-2.6.15-54-386
  56.4GB: boot/vmlinuz-2.6.15-55-386
  56.4GB: initrd.img
  56.4GB: initrd.img.old
  56.3GB: vmlinuz
  56.4GB: vmlinuz.old


```

---

### Post by oldfred on 2010-04-22
What kernels do you have in your system now? I show 2.6.15 series is Dapper Drake?

You still have parts of grub and grub2.

---

### Post by whitewalls on 2010-04-26
I have the 2.6.15 kernel in /boot/, and then just one called vmlinuz.  I know I have parts of grub2, I've been trying most anything I can... I think at one point I tried installing grub2.  I feel like I just need to reinstall... just trying to avoid it as long as I can, haha :\

> **oldfred said:**
> What kernels do you have in your system now? I show 2.6.15 series is Dapper Drake?

You still have parts of grub and grub2.

---

### Post by oldfred on 2010-04-26
I found the right command to get the latest kernel downloaded. If you chroot into your system this will uninstall grub & grub2 and do a full update and the dist update which downloads the latest kernel.

Do not copy any thing with #

sudo -i
mount /dev/sda1 /mnt
mount --bind /dev  /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys  /mnt/sys
mount --bind /usr/ /mnt/usr
chroot /mnt
sudo -i
apt-get update
apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda
#Exit by pressing CTRL-d.
umount /mnt/dev /mnt/proc /mnt/sys /mnt/usr 
umount /mnt
#Reboot & run:
sudo update-grub

---

### Post by whitewalls on 2010-04-27
> **oldfred said:**
> I found the right command to get the latest kernel downloaded. If you chroot into your system this will uninstall grub & grub2 and do a full update and the dist update which downloads the latest kernel.


oldfred,

I tried what you suggested, but still no luck.  I ended up just reinstalling/formating.  I'm not sure what I did to cause this problem, but hopefully I can avoid doing it again!

Thanks for helping me out, though!  I appreciate it.

---

