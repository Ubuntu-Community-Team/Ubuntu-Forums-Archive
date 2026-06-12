---
title: "Lucid Startup Error 101"
date: 2010-05-01
forum: General Help
---

### Post by daveysan on 2010-05-01
Hi. I upgraded my Karmic OS to Lucid the day after it became available and have been having some troubles - can anyone help? I am having trouble starting the OS. Brief history:
I have real troubles with the ATI graphics and spent a while trying (finally successfully) to remove fglrx and associated dependencies. I then rebooted ready to install new drivers. I now get the following error on startup:

CIFS VFS Error connecting to socket - aborting connection
CIFS VFS cifs_mount failed w/return code (-101)

For the last couple of weeks or so, I have noticed CFS errors on shutdown which has meant that I have needed to physically press the off button to turn the machine off, but since I could still operate I left that problem on the back burner "for when I have more time". Don't know if the two problems are related. 

Anyway, I am currently in the situation where I cannot start Ubuntu at all unless I use the install CD and try the LIVE distro.

My fstab file looks like this:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

Any ideas?

(My PC Has a 1 TB drive and a 500 gig drive. The 1 TB drive has dual boot Vista (came preinstalled and I have a couple of games for it - else, yuk) and Linux. The 500 gig drive is a data drive).

I'd rather not reinstall from scratch though may have to? I don't know of any way to repair-install the OS - maybe that would be possible too?

Thanks in advance for any help

---

### Post by oldfred on 2010-05-01
Your fstab shows swap but no root??? or is that the fstab from the liveCD?

run this to see if everything else is there or not.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by daveysan on 2010-05-02
Hi Oldfred. Thanks for the post. Yes, the fstab I posted was for the liveCD ... I should have thought about that. 

Here is the output from the boot script ...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,524,616,694 1,524,614,647   7 HPFS/NTFS
/dev/sda2       1,524,616,695 1,953,520,064   428,903,370   5 Extended
/dev/sda5       1,524,616,758 1,936,041,344   411,424,587  83 Linux
/dev/sda6       1,936,041,408 1,953,520,064    17,478,657  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,769,023   976,766,976   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        845C4B115C4AFD84                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e4f161ab-7895-4e15-8792-b946ba2cee07   ext3                                     
/dev/sda6        83735cf4-546b-4ba2-8e80-83a0b6ab67a1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2064F9CD64F9A626                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
timeout		10

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
# kopt=root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=e4f161ab-7895-4e15-8792-b946ba2cee07

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-19-generic
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-19-generic (recovery mode)
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-16-generic
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-16-generic (recovery mode)
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-15-generic
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-15-generic (recovery mode)
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=e4f161ab-7895-4e15-8792-b946ba2cee07 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		e4f161ab-7895-4e15-8792-b946ba2cee07
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda5
UUID=e4f161ab-7895-4e15-8792-b946ba2cee07  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda6
UUID=83735cf4-546b-4ba2-8e80-83a0b6ab67a1  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
//192.168.0.111/share /home/dave/backups2 smbfs rw,dave,username=dpaine,password=password
/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1               0  0  
/dev/sda1                                  /media/sda1    ntfs         nls=iso8859-1               0  0  

=================== sda5: Location of files loaded by Grub: ===================


 834.8GB: boot/grub/menu.lst
 834.6GB: boot/grub/stage2
 834.6GB: boot/initrd.img-2.6.28-16-generic
 835.0GB: boot/initrd.img-2.6.31-14-generic
 955.9GB: boot/initrd.img-2.6.31-15-generic
 836.1GB: boot/initrd.img-2.6.31-16-generic
 838.1GB: boot/initrd.img-2.6.31-17-generic
 959.6GB: boot/initrd.img-2.6.31-19-generic
 841.3GB: boot/initrd.img-2.6.31-20-generic
 962.4GB: boot/initrd.img-2.6.31-21-generic
 962.6GB: boot/initrd.img-2.6.32-21-generic
 834.7GB: boot/vmlinuz-2.6.28-16-generic
 834.7GB: boot/vmlinuz-2.6.31-14-generic
 835.0GB: boot/vmlinuz-2.6.31-15-generic
 954.8GB: boot/vmlinuz-2.6.31-16-generic
 836.2GB: boot/vmlinuz-2.6.31-17-generic
 959.6GB: boot/vmlinuz-2.6.31-19-generic
 955.6GB: boot/vmlinuz-2.6.31-20-generic
 839.5GB: boot/vmlinuz-2.6.31-21-generic
 959.2GB: boot/vmlinuz-2.6.32-21-generic
 962.6GB: initrd.img
 962.4GB: initrd.img.old
 959.2GB: vmlinuz
 839.5GB: vmlinuz.old
```

---

### Post by daveysan on 2010-05-02
Hi. Interesting update:

I just tried starting from a previous kernel (2.6.31-21-generic) and was able to start Ubuntu without  problems. So I used that session to fix up the graphics card issues I was having and then tried to reboot back into the old kernel (2.6.32-21-generic) - expecting it to fail  ... but it didn't! 

So, my problem seems to have been fixed by simply restarting with a previous kernel and then starting again with the latest kernel. Oldfred - thank you very much for looking at the issue :P I still get the CIFS error, which is odd, so I'd still be interested in knowing what has happened to my system, but the fact that it boots nicely is great.
:guitar:

Interestingly, my graphics problems (unable to enable visual effects) return with the later kernel. So for now I'll stick with the working one :-) If there is a bug in my kernel I am happy to help trouble shoot it.

---

### Post by cjlindem on 2010-05-02
I am getting this error also.  Rebooting and using the previous kernel for one boot, then reverting to the current kernel did not fix it for me.  It's funny, it's the same sort of error I used to get at shutdown.  In 10.04 my shutdown goes super fast and with no errors, but the cifs error happens at boot time now.  Also strange, is that the mapping to my windows server is fine once I'm to the desktop

---

### Post by daveysan on 2010-05-02
cjlindem - do you have different disks that you auto mount? One thing I plan to do is try stopping their automount to see if that stops the cifs error. Seems I am getting "unknown mount option" and I am wondering if the 101 error relates to that.

There is a program called pysdm that you can use to disable disks from auto mount. I'll report back to this thread once I have tried this ...

Also, it seems there was a last minute fix in Lucid to an eror with systems with Windoze on (I have this) that could prevent dual boot from working. I wonder if this is perhaps related.

---

### Post by dino99 on 2010-05-02
fglrx is the main problem, dig around fglrx+radeon+uninstalling

---

### Post by cjlindem on 2010-05-02
Daveysan,  I commented out the line in my fstab responsible for mounting via cifs to my windows server.  This did eliminate the error at boot time. It also eliminated my mapping to the server.  I really have to wonder if this is a bug and is throwing a false error, seeing as the mount IS completed successfully and available from my desktop.  The error message would give every indication that the map -wasn't- successful.

---

### Post by oldfred on 2010-05-02
I do not see anything unusual in your results.txt. Perhaps Lucid boots so quick now, that even though the network is up the server has not had a chance to respond, so the mount in fstab does not work? Just a guess.

The last minute fix in Lucid was to make sure windows would boot on first reboot. It missed it on the first part of the install, and required users to run the sudo update-grub to find it and put it into the grub menu. They delayed it as they did not want users to have to run the update as they might think they lost windows.

---

### Post by daveysan on 2010-05-02
oldfred - I wasn't specifically mounting any network drives - just internal ones, though it is good to know results.txt looked ok :) Are you one of the Ubuntu developers. If so - hats off to you and your colleagues. Each release just gets so much better. Yes - it may have problems, but it isn't as if Doze doesn't ;)

dino99 - I suspect you are right - it was after uninstalling fglrx that I had the problem - though it could have been a coincidence. I had real troubles uninstalling fglrx, though when I managed it and used the supplied drivers all worked well.

cjlindem - Agreed completely. Very odd. Good that you can now boot too :)

---

### Post by oldfred on 2010-05-02
I saw this so I thought you had a network drive being mounted.
//192.168.0.111/share /home/dave/backups2 smbfs rw,dave,username=dpaine,password=password


No I am not a developer, I am retired and always liked fixing computer problems, since CP/M days. I have had no issues with Karmic and did have to add a nomodeset on Lucid, but I am only testing lucid now so I have not done a lot with it.

---

### Post by daveysan on 2010-05-03
Yes, you are right - I had forgotten about that little puppy. My response was based on the output of pysdm, but at that time I had removed the share (it is a backup NAS, but I don't have the NAS on often). Loving the new stuff in Lucid ...

---

