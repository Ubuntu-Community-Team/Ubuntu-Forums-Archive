---
title: "Desperate! Startup-Manager wiped my menu.lst"
date: 2010-03-17
forum: General Help
---

### Post by distortedecho on 2010-03-17
Hi,

I need some serious expert help.

Startup-Manager wiped my menu.lst and now all I get is the grub command line.

I type:

```
root (hd0,5)
```
Then
```
setup (hd0)
```
Then
```
Kernel /boot/vmlinuz ... etc... 20-generic
```
&
```
Initrd /boot/init ... etc.. 20-generic
```
and finally
```
boot
```

But it gets bored of waiting and goes to the initramfs command line. I have no idea what to do at this point.

I then try to use the Live Boot CD to try and reinstall Grub or Startup-Manager but can't get into an OS. It goes through the motions and then gives me an endless stream of "Buffer I/O error"

Can someone please help me get back into 9.10 and how to rescue Grub??

---

### Post by zvacet on 2010-03-17
Did you tried [https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode)

---

### Post by distortedecho on 2010-03-17
I have grub legacy.

---

### Post by spyrule on 2010-03-17
Could you write out the full code you're using for kernel and initrd?

---

### Post by distortedecho on 2010-03-17
> **spyrule said:**
> Could you write out the full code you're using for kernel and initrd?
It's the latest kernal which is (I think)(I tabbed to auto complete)

```
 kernel /boot/vmlinuz-2.6.31-20-generic
```
```
 initrd /boot/initrd.img-2.6.31-20-generic
```

I've also tried the ro splash quiet switches... no difference.

---

### Post by spyrule on 2010-03-17
Its been a while since I've had to do something like this... But, I remember needing the  root=/dev/hda1 at the end of the kernel line... If you remember which one it is.

If that's not the case, you can d/l grub and put it on an external drive or a floppy if you have access to those things... See [here]("http://www.troubleshooters.com/linux/grub/grub.htm") for a bit more detail.

---

### Post by distortedecho on 2010-03-17
> **spyrule said:**
> Its been a while since I've had to do something like this... But, I remember needing the  root=/dev/hda1 at the end of the kernel line... If you remember which one it is.

If that's not the case, you can d/l grub and put it on an external drive or a floppy if you have access to those things... See [here]("http://www.troubleshooters.com/linux/grub/grub.htm") for a bit more detail.

I've tired using root=UUID= w/e and that didn't work.
I presume that's the same thing?

---

### Post by spyrule on 2010-03-17
Should be, as long as the UUID is right. Is it possible to use an external drive or a floppy to load a grub on to... Having had so many issues with programs trying to pirate the grub settings, I ended up putting the grub on a small partition on my system and it works great.

---

### Post by distortedecho on 2010-03-17
I have a second hhd for storage.

---

### Post by sisco311 on 2010-03-17
Boot a Live CD & reinstall grub:
[uhelp]/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB[/uhelp]

but:
```
root (hd0,5)
kernel /boot/vmlinuz... root=/dev/sda6 ro
initrd /boot/initrd.img... 
boot

```

should boot Ubuntu.

---

### Post by distortedecho on 2010-03-17
> **sisco311 said:**
> Boot a Live CD & reinstall grub:
[uhelp]/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB[/uhelp]

but:
```
root (hd0,5)
kernel /boot/vmlinuz... root=/dev/sda6 ro
initrd /boot/initrd.img... 
boot

```

should boot Ubuntu.

The live cd won't load. I get Buffer Error's.

---

### Post by distortedecho on 2010-03-17
> **sisco311 said:**
> Boot a Live CD & reinstall grub:
[uhelp]/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB[/uhelp]

but:
```
root (hd0,5)
kernel /boot/vmlinuz... root=/dev/sda6 ro
initrd /boot/initrd.img... 
boot

```

should boot Ubuntu.

I tried adding root-/dev etc..

nd it got bored again and gives me initramfs prompt :(

---

### Post by wilee-nilee on 2010-03-17
I would use this boot info script to post on the forum so we can see everything involved such as boot location, partitions, and OS.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Down load it to your desktop and use to generate the script and post, the 3 people who regularly help people with this will generally be on line in a couple of hours probably.

---

### Post by distortedecho on 2010-03-17
I can try that.

But, I finlly got the Live CD to work, tried purging grub, reinstall and also tried to install grub-pc. Still get grub command on boot.

I then booted Hirens and tried Boot Magic. Told it which drive had the OS - still got grub command on boot...

Should I continue with the script?

---

### Post by distortedecho on 2010-03-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb6 and 
                       looks at sector 86302414 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xabb7ffe0

Partition  Boot         Start           End          Size  Id System

/dev/sda2                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x844b844b

Partition  Boot         Start           End          Size  Id System

/dev/sdb2              16,065   488,392,064   488,376,000   f W95 Ext d (LBA)
/dev/sdb5              16,128     5,381,774     5,365,647  83 Linux
/dev/sdb6           5,381,838   485,420,039   480,038,202  83 Linux
/dev/sdb7         485,420,103   488,392,064     2,971,962  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        5E407F3E407F1C49                       ntfs       Storage                       
/dev/sdb5        db6df7bf-9981-42a3-b7ca-47fa27d659ff   ext3                                     
/dev/sdb6        ed298760-5672-4486-87ba-3fc395b40e6a   ext3                                     
/dev/sdb7        febf56c9-488d-4738-91f5-ef054f686c36   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb6/boot/grub/menu.lst: ===========================

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
timeout		2

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=ed298760-5672-4486-87ba-3fc395b40e6a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ed298760-5672-4486-87ba-3fc395b40e6a

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
# howmany=0

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

### END DEBIAN AUTOMAGIC KERNELS LIST




=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb6 :
UUID=ed298760-5672-4486-87ba-3fc395b40e6a / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb7 :
UUID=febf56c9-488d-4738-91f5-ef054f686c36 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda2 /media/Storage ntfs-3g defaults,locale=en_GB.UTF-8 0 0

=================== sdb6: Location of files loaded by Grub: ===================


  44.1GB: boot/grub/menu.lst
  44.1GB: boot/grub/stage2
  44.1GB: boot/initrd.img-2.6.31-14-generic
  44.2GB: boot/initrd.img-2.6.31-15-generic
  44.1GB: boot/initrd.img-2.6.31-16-generic
  44.1GB: boot/initrd.img-2.6.31-17-generic
  44.1GB: boot/initrd.img-2.6.31-19-generic
  44.1GB: boot/initrd.img-2.6.31-20-generic
  44.1GB: boot/vmlinuz-2.6.31-14-generic
  44.1GB: boot/vmlinuz-2.6.31-15-generic
  44.2GB: boot/vmlinuz-2.6.31-16-generic
  44.2GB: boot/vmlinuz-2.6.31-17-generic
  44.2GB: boot/vmlinuz-2.6.31-19-generic
  44.1GB: boot/vmlinuz-2.6.31-20-generic
  44.1GB: initrd.img
  44.1GB: initrd.img.old
  44.1GB: vmlinuz
  44.2GB: vmlinuz.old
```

---

### Post by zvacet on 2010-03-17
If you have working live CD and you want to reinstall grub follow [this]("http://ubuntuforums.org/showthread.php?t=224351") guide.

---

### Post by wilee-nilee on 2010-03-18
bump

---

### Post by distortedecho on 2010-03-18
> **zvacet said:**
> If you have working live CD and you want to reinstall grub follow [this]("http://ubuntuforums.org/showthread.php?t=224351") guide.
I've tired installing Grub and Grub 2 and a 3rd party MBR manager - all I get is the grub command line.

I'm going to try the Ubuntu Alternative CD and install Grub from that.

wilee - who are the people who help with this sort of thing? Maybe I can PM them? Thanks

---

### Post by zvacet on 2010-03-18
> wilee - who are the people who help with this sort of thing?

Any Ubuntu forum member who think that can help you with advice,suggestion,solution...

Don't PM because if you get answer on forum other people with same problem will be able to find solution.Mark thread as solved when you get right answer and that will help others.

---

### Post by distortedecho on 2010-03-18
> **zvacet said:**
> Any Ubuntu forum member who think that can help you with advice,suggestion,solution...

Don't PM because if you get answer on forum other people with same problem will be able to find solution.Mark thread as solved when you get right answer and that will help others.

I realise my comment didn't come out right! lol

Basically wille mentioned there are some members that specialise... I was asking for there forum names. I would of course direct them to this thread :)

---

### Post by distortedecho on 2010-03-18
Excellent! I've fixed it!

Put the following in menu.lst:

```
title   Ubuntu 9.10
root   (hd0,5)
kernel   /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb6
initrd   /boot/initrd.img-2.6.31-20-generic
```

Works - but I don't have a splash screen, but I'm sure I can fix that also.

Thanks - wilee-nilee - that script really came in useful!!!

---

### Post by sisco311 on 2010-03-18
> **distortedecho said:**
> Excellent! I've fixed it!

Put the following in menu.lst:

```
title   Ubuntu 9.10
root   (hd0,5)
kernel   /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb6
initrd   /boot/initrd.img-2.6.31-20-generic
```


cool!

> **distortedecho said:**
> 
Works - but I don't have a splash screen, but I'm sure I can fix that also.



append the kernel line with **ro quiet splash**:
```
kernel   /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb6 ro quiet splash
```

---

### Post by distortedecho on 2010-03-20
> **sisco311 said:**
> cool!




append the kernel line with **ro quiet splash**:
```
kernel   /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb6 ro quiet splash
```

Done!

---

