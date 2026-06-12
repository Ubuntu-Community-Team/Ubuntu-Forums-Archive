---
title: "New GRUB Problem"
date: 2009-10-28
forum: General Help
---

### Post by Dan Again on 2009-10-28
Okay, so I was having some problems with GRUB, which I outlined in [this]("http://ubuntuforums.org/showthread.php?t=1301718") post.

I edited GRUB so that I am now able to log into Ubuntu again, but now I can't get into Windows!

Here is my menu.lst

```
## ## End Default Options ##

title		Ubuntu 9.04 (Jaunty Jackalope) 
uuid		236a02cc-ee55-4b35-82be-681b6fc72421
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=236a02cc-ee55-4b35-82be-681b6fc72421 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic 
quiet 

title Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST
```

When I select Windows XP from the GRUB it says...

> Starting up...
Loading GRUB stage 2

Then it just rolls right back to the GRUB menu. I played around a little bit with [Super GRUB Disk]("http://www.supergrubdisk.org/") disk a little bit while trying to fix my ability to boot into Linux, but I didn't think I messed with my Windows partition at all.

Anyone have any thoughts?

---

### Post by Dan Again on 2009-10-28
Does anyone have ideas as to what might be causing this problem? I'm perplexed because I really didn't alter the Windows part of menu.lst. Furthermore, I don't understand where the reference to GRUB Stage2 is coming from. Can anyone offer some insight?

---

### Post by SteveDee on 2009-10-28
> **Dan Again said:**
> Does anyone have ideas as to what might be causing this problem? I'm perplexed because I really didn't alter the Windows part of menu.lst. Furthermore, I don't understand where the reference to GRUB Stage2 is coming from. Can anyone offer some insight?

Basically Grub is a 2 stage process. Stage1 resides in the boot sector. Because this is only 512bytes, instructions in Stage1 call the rest of Grub (i.e. Stage2).

More info here: [http://www.gnu.org/software/grub/manual/grub.html#Images](http://www.gnu.org/software/grub/manual/grub.html#Images)

---

### Post by louieb on 2009-10-28
Hope when you were trying to fix the original problem you did not run [COLOR=Red]setup (hd0,1)[/COLOR] at any time. If you did you will need a Vista recovery CD. [Vista Recovery Disc &#8212; NeoSmart]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or Vista install CD. (anyway I think its Vista - which flavor of windows are you trying to fix).

Go ahead ad post a new results.txt  from the [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 

From looking at the original results.txt looks like that disk is littered of old Linux and windows installs - don't know how you keep them all straight.

---

### Post by Dan Again on 2009-10-28
I did run setup (hd0,1), but luckily I have Windows recovery discs. Here is the result of boot_info_script...

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 142738062 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 142738062 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 142738062 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda6 and 
                       looks at sector 142738062 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda7 and 
                       looks at sector 142738062 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda8 and 
                       looks at sector 142738062 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda4 and 
                       looks at sector 142738062 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3242a3f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    25,167,871    25,165,824  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    86,606,414    61,432,560   7 HPFS/NTFS
/dev/sda3          86,606,415   617,699,249   531,092,835   5 Extended
/dev/sda5          86,606,478   148,055,039    61,448,562  83 Linux
/dev/sda6         148,055,103   209,487,599    61,432,497  83 Linux
/dev/sda7         209,487,663   613,972,169   404,484,507  83 Linux
/dev/sda8         613,972,233   617,699,249     3,727,017  82 Linux swap / Solaris
/dev/sda4         617,705,472   625,139,711     7,434,240  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D682289882287EDD" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda5: UUID="236a02cc-ee55-4b35-82be-681b6fc72421" TYPE="ext3" 
/dev/sda6: LABEL="LINUX 2" UUID="7dc07c0d-68f7-48fc-b30b-0e12fc81cb77" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="22604c03-931d-4768-a9f2-86a25d1df1a0" TYPE="ext3" 
/dev/sda8: UUID="2fbc3429-5881-4471-91bd-119ef666836e" TYPE="swap" 

=============================== "mount" output: ===============================

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
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
/dev/sda7 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dan)


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
timeout		30

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
# kopt=root=UUID=236a02cc-ee55-4b35-82be-681b6fc72421 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=236a02cc-ee55-4b35-82be-681b6fc72421

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

title		Ubuntu 9.04 (Jaunty Jackalope) 
uuid		236a02cc-ee55-4b35-82be-681b6fc72421
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=236a02cc-ee55-4b35-82be-681b6fc72421 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic 
quiet 

title Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=236a02cc-ee55-4b35-82be-681b6fc72421 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=22604c03-931d-4768-a9f2-86a25d1df1a0 /home           ext3    relatime        0       2
# /dev/sda8
UUID=2fbc3429-5881-4471-91bd-119ef666836e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  54.8GB: boot/grub/menu.lst
  73.0GB: boot/grub/stage2
  73.1GB: boot/initrd.img-2.6.27-11-generic
  73.1GB: boot/initrd.img-2.6.28-11-generic
  74.3GB: boot/initrd.img-2.6.28-13-generic
  53.9GB: boot/initrd.img-2.6.28-14-generic
  53.8GB: boot/initrd.img-2.6.28-15-generic
  74.7GB: boot/initrd.img-2.6.28-16-generic
  73.0GB: boot/vmlinuz-2.6.27-11-generic
  73.1GB: boot/vmlinuz-2.6.28-11-generic
  54.6GB: boot/vmlinuz-2.6.28-13-generic
  59.5GB: boot/vmlinuz-2.6.28-14-generic
  74.2GB: boot/vmlinuz-2.6.28-15-generic
  54.2GB: boot/vmlinuz-2.6.28-16-generic
  74.7GB: initrd.img
  53.8GB: initrd.img.old
  54.2GB: vmlinuz
  74.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

So what exactly did I do when I ran setup (hd0,1)? I also ran setup (hd0,2), (hd0,3), (hd0,4), (hd05), (hd0,6) and (hd0,7)...did doing that muck other things up that I should be aware of?

Thanks, Louie

---

### Post by oldfred on 2009-10-28
You somehow managed to install grub into every partition. It only needs to be in the MBR (hd0) and if you have many operating systems and want to chainboot you also install it to the partition you want to boot from (hd0,4). All the others do not need grub, but I do not know a way to remove it and I do not think it matters except for the windows partition. Windows also is a chainboot but must have its boot in the windows partition.

The partition hd0,1 needs also to have windows boot into it. The normal repair of windows are two commands one fixes the mbr and the other fixes the partition.

This set of commands total recovers windows, I do not know if you can run just the fixboot and solve your problem. If not do the total fix, make sure windows boots, then reinstall grub to the MBR.

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1. Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

---

### Post by egalvan on 2009-10-28
> **Dan Again said:**
> 

I edited GRUB

Here is my menu.lst

```
## ## End Default Options ##

title		Ubuntu 9.04 (Jaunty Jackalope) 
uuid		236a02cc-ee55-4b35-82be-681b6fc72421
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=... 
initrd		/boot/initrd.img-2.6.28-16-generic 
quiet 

[COLOR="Red"]title Windows XP[/COLOR]
root (hd0,1)
savedefault
makeactive
chainloader +1


### [COLOR="Red"]END DEBIAN AUTOMAGIC KERNELS LIST[/COLOR]
```

?

As an aside, the XP stanza should not be inside the DEBIAN AUTOMATIC KERNELS LIST.
It should be placed *after*.

---

### Post by Dan Again on 2009-10-28
I am not exactly sure what you are talking about, Fred. If I follow your steps will I have to do some more stuff to be able to access Linux again? What will happen when I turn on my computer after I follow your steps?

Furthermore, my computer has a Windows Recovery partition and I am worried that I may have messed that up to. Do you think that is the case? If so, do you know a way I could go about fixing it?

---

### Post by louieb on 2009-10-28
Well the setup command hosed the boot sector. (hd0,1) is sda2

```

sda2: __________________________________________________  
    File system:       
    Boot sector type: [COLOR=Red] Grub[/COLOR]
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 142738062 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 

```One thing that looks like trouble for sda2 not sure how to fix this. Have not see overwriting a partitions boot sector make it unusable before. Usually you can still read the contents but can't boot the OS in it. 

```
Mounting failed:
mount: unknown filesystem type ''
```Still need to know which windows version - Vista and Win7 get fixed a little different from win XP. 

I'm guessing Vista. 

Anyway with Vista boot the recovery CD - option R for recovery console. 

```
c:
bootrec.exe  /fixboot
```tech stuff : [Bootrec.exe tool Vista (MS support)]("http://support.microsoft.com/kb/927392")

---

### Post by Dan Again on 2009-10-28
Running Vista

Will following your advice cause anything with Linux to get messed up?

Thanks so much for your help. Go Texas!

---

### Post by louieb on 2009-10-28
No guarantee that trying to fix Vista will leave the Linux install unharmed. But it should not touch the Linux install.  

> Furthermore, my computer has a Windows Recovery partition and I am worried that I may have messed that up to

Maybe you did. Again looking at the original results.txt  looks like sda4 or sda1 is the recovery partition - sda1 looks good - but sda4 has the same problem as sda2. 

Just hope the recovery partition is sda1. 

Anyway the next thing I would try is the Vista recovery console and try the bootrec.exe fix.  If that does not work you may be looking at a re-install.

Can you browse your Vista install from Ubuntu? - that would be a good sign if you can.      


lol I'm a transplanted Okie - root for Texas :grin:because one of my kids is going to school there.

---

### Post by Dan Again on 2009-10-29
Awesome. I really don't care about my Windows partition that much as I barely ever use it. Just like to have it as a safety net for instances when I mess up Linux...like I did with the earlier GRUB problem I was having. Definitely want to get it fixed ASAP and I TOTALLY appreciate your help, just not freaking out like I was with the Linux problem. I may not have a chance to try your fix for a few days (just coming off two days off from work), but I will definitely be in touch as to how it worked.

That's awesome that your kid goes to UT...I went there for a year before going to culinary school. Moving back to Austin for a semester (Austin Community College) in January...so excited!

---

### Post by Dan Again on 2009-11-08
This worked perfectly! Took two seconds and didn't touch Linux. Thanks, Louie...hook 'em!

---

