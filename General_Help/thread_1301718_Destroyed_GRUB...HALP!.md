---
title: "Destroyed GRUB...HALP!"
date: 2009-10-26
forum: General Help
---

### Post by Dan Again on 2009-10-26
In an attempt to edit my GRUB menu I completely destroyed my ability to log in to Ubuntu. The Linux menu items that I have listed point to old Linux kernels that are no longer on my system. I know that I can edit boot option entries through the GRUB, but I have no idea what the correct information is or how to find it. Can someone help me, please?

---

### Post by prem1er on 2009-10-26
I'm guessing you didn't make a backup of the file before you made changes? If not I would post is currently in the file so that someone may help you.

---

### Post by bruno9779 on 2009-10-26
Do you have only ubuntu installed there?

Anyway, boot to the live CD desktop and in a terminal:

```
grub
```

then, in grub:

```
find /boot/grub/stage1
```

this gives you an output like(hd0,1). Use that for the next 2 commands:

```
root (hdx,y)
setup (hdx)
```

reboot and you should be good to go.

---

### Post by Dan Again on 2009-10-26
@prem1er - I did not make a back up. Will not make that mistake again. You are advocating for me to post the incorrect information that the GRUB is currently pointing to?

@bruno9779 - Will that update the kernel information or just the device information?

---

### Post by bruno9779 on 2009-10-26
> **Dan Again said:**
> @prem1er - I did not make a back up. Will not make that mistake again. You are advocating for me to post the incorrect information that the GRUB is currently pointing to?

@bruno9779 - Will that update the kernel information or just the device information?

It creates menu.lst anew, so if you didn't mess with vmlinuz simlinks, you should be fine.

It is a very unintrusive operation, so if it does not work, it is unlikely to mess up your system. just give it a go

---

### Post by Dan Again on 2009-10-26
Thanks!

---

### Post by bruno9779 on 2009-10-27
> **Dan Again said:**
> Thanks!

If it worked please mark the post as solved

---

### Post by Dan Again on 2009-10-27
About to try now...will let you know!

---

### Post by Dan Again on 2009-10-27
Okay...it is not working. I am working on Ubuntu running off my LiveCD now. I open terminal, type "grub" and then type "find /boot/grub/stage1"...it says Error 15, file not found.

I'm fairly certain that the problem is due to the fact that the file I'm looking for is on a different partition, my /home partition, but I'm not quite sure how to get it to point there properly. I tried mounting that partition and moving to that directory in the terminal, but that didn't work. Any ideas?

---

### Post by Dan Again on 2009-10-27
Is there anyone else out there who might be able to help me with this?

---

### Post by Dan Again on 2009-10-27
Okay, so I managed to get bruno9779's suggestion to work by starting with "sudo grub" I run "setup (hdx)" and see an output like something has happened, but then when I restart my computer the GRUB has not changed.

HALP!

---

### Post by bruno9779 on 2009-10-27
let's see.

Grub and all the booting stuff is not in your /home directory. It is in /boot.

I am not too sure what is it that you have done with the kernels, but you should at least make sure you have one in your /boot folder:

```
-rw-r--r-- 1 root root  623709 2009-10-16 17:12 abi-2.6.31-14-generic
-rw-r--r-- 1 root root  105768 2009-10-16 17:12 config-2.6.31-14-generic
drwxr-xr-x 2 root root    4096 2009-10-25 00:42 grub
-rw-r--r-- 1 root root 7866011 2009-10-26 12:41 initrd.img-2.6.31-14-generic
-rw-r--r-- 1 root root  128796 2009-10-23 17:24 memtest86+.bin
-rw-r--r-- 1 root root 2130808 2009-10-16 17:12 System.map-2.6.31-14-generic
-rw-r--r-- 1 root root    1336 2009-10-16 17:18 vmcoreinfo-2.6.31-14-generic
-rw-r--r-- 1 root root 3941696 2009-10-16 17:12 vmlinuz-2.6.31-14-generic

```

the kernel is vmlinuz.

Error 15 in grub is "file not found".
try reinstalling grub altogether:

```
sudo apt-get install grub
```

PS: can you please post the content of your /boot folder and of /boot/grub/menu.lst?

PPS: are you on jaunty or karmic?

---

### Post by bruno9779 on 2009-10-27
wait a minute.

did you run setup (hdx)?????? 

"x" must be replaced with the output of the find command "find".

so it must be:

setup (hd0)
setup (hd1)
....

the number of the hard disk where ubuntu is installed

Same goes for root command:

root (hd0,1)
root (hd1,1)

whatever. It depends from the output of 

```
find /boot/grub/stage1
```

---

### Post by louieb on 2009-10-27
need information about your setup. please follow [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") 
and put the results in your next post. 

if all you did was mess around with your menu.lst then another option is [Super Grub Disk]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html")- it should be able to boot Ubuntu.

---

### Post by Dan Again on 2009-10-28
Okay, so I have used Super Grub Disk to boot my Linux partition...it feels so good to be back! Unfortunately, the methods that people have told me to use to restore my menu.lst do not seem to be working. Super Grub Disk's restore features do not seem to work either.

Louie when I type "sudo bash ~/Desktop/boot_info_script*.sh" it returns "bash: /home/dan/Desktop/boot_info_script*.sh: No such file or directory"

Now that I am back on my Linux partition it should be very easy to edit menu.lst, the problem is I do not know the proper information to put. Anyone?

---

### Post by Dan Again on 2009-10-28
Okay...missed the first part of the tutorial about actually DOWNLOADING Boot Info Script. Forgive me. D/l'ing it now...

---

### Post by Dan Again on 2009-10-28
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

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3242a3f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    25,167,871    25,165,824  27 Hidden HPFS/NTFS
/dev/sda2          25,173,855    86,606,414    61,432,560   7 HPFS/NTFS
/dev/sda3          86,606,415   617,699,249   531,092,835   5 Extended
/dev/sda5          86,606,478   148,055,039    61,448,562  83 Linux
/dev/sda6         148,055,103   209,487,599    61,432,497  83 Linux
/dev/sda7         209,487,663   613,972,169   404,484,507  83 Linux
/dev/sda8         613,972,233   617,699,249     3,727,017  82 Linux swap / Solaris
/dev/sda4    *    617,705,472   625,139,711     7,434,240  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D682289882287EDD" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="5058205B58204258" LABEL="ACER" TYPE="ntfs" 
/dev/sda4: UUID="165818D05818B10B" TYPE="ntfs" 
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
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda7 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dan)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=dan)


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

title		Ubuntu Recovery Mode 
uuid		236a02cc-ee55-4b35-82be-681b6fc72421 
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=236a02cc-ee55-4b35-82be-681b6fc72421 ro  single 
initrd		/boot/initrd.img-2.6.28-16-generic 

title Windows XP 
root (hd0,1) 
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


  74.2GB: boot/grub/menu.lst
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

================================ sda4/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=768

=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by Dan Again on 2009-10-28
I don't understand why I can't get any of these methods to work for me. When I follow the steps outlined in [this]("http://ubuntuforums.org/showthread.php?t=224351") thread it says I am successful, but GRUB does not change up reboot.

I open terminal, type "sudo grub" and then "find /boot/grub/stage1" which generates the response "hd0,4" so I type "root (hd0,4)" and then "setup (hd0)" I get a message back saying success...it looks like everything works, but then like I said, nothing changes when I restart. I've even tried replacing "setup (hd0)" with "setup (hd0,#)" where "#" is every number 1 through 7 thinking that this might help things per the first edit in the above mentioned post, but nothing seems to change. I should add that when I use "setup (hd0,#)" I get an indication that the operation was not 100% successful.

The GRUB restore options through the Super Grub CD that I downloaded do not seem to work either.

I feel like all I really need is where to find the proper information to put into menu.lst...I am fine editing it by hand, just don't know what to put.

Can someone help me?

---

### Post by Dan Again on 2009-10-28
[IMG]http://www.danforbes.info/Screenshot.png[/IMG]

Don't know if this helps...

---

### Post by teward on 2009-10-28
Have you tried just reinstalling GRUB from scratch?  if you just install GRUB, it SHOULD over-write your current GRUB install, and maybe it will fix it.  But I've never had to deal with this, just recovering GRUB after a Windows installation re-wrote the boot loader on the drive, so I might be completely wrong. **(NOTE: I don't know how to install GRUB from scratch, other users who know more than I do, please comment on this topic)**

---

### Post by Dan Again on 2009-10-28
I did run sudo apt-get install grub per Bruno's instructions, but nothing changed...I think because I already have GRUB installed on my system. I am nervous to delete GRUB, but if someone is familiar with this technique and confident that it will work, then I am happy to try it.

---

### Post by georgelenzer on 2009-10-28
Do this:

```
cat /boot/grub/menu.lst
```

Post the results here.  I'll see what I can do to help.

---

### Post by Dan Again on 2009-10-28
## ## End Default Options ##

title		Ubuntu 9.04 (Jaunty Jackalope) 
uuid		236a02cc-ee55-4b35-82be-681b6fc72421 
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=236a02cc-ee55-4b35-82be-681b6fc72421 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic 
quiet 

title		Ubuntu Recovery Mode 
uuid		236a02cc-ee55-4b35-82be-681b6fc72421 
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=236a02cc-ee55-4b35-82be-681b6fc72421 ro  single 
initrd		/boot/initrd.img-2.6.28-16-generic 

title Windows XP 
root (hd0,1) 
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST

Thanks, George. You might also want to take a look at the results from boot_info_script that I posted as well as the screenshot I took of my boot folder. I really appreciate your help.

---

### Post by tuahaa on 2009-10-28
Its time for a motivational pic.[IMG]http://img4.yfrog.com/img4/5114/poster90186956.jpg[/IMG]

---

### Post by Dan Again on 2009-10-28
LOLOLOL...thanks, that helps.

---

### Post by tuahaa on 2009-10-28
I hope you fix it though lol

---

### Post by Dan Again on 2009-10-28
Fixed it! It was a combination of Super GRUB and boot_info_script that allowed me to fix this problem.

Super GRUB allowed me to log into my Linux partition, which gave me the ability to edit menu.lst

boot_info_script gave me the information I needed to rewrite menu.lst...it just took some playing I guess.

Thanks, everyone!

---

