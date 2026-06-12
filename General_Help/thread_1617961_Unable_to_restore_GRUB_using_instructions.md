---
title: "Unable to restore GRUB using instructions"
date: 2010-11-10
forum: General Help
---

### Post by avalook on 2010-11-10
I have a dual boot system with Ubuntu 10.10 and Windows Vista. Today I upgraded Vista to Windows 7, and GRUB is no longer working. The usual problem, I know. Searched forums & Web and found many instructions for restoring GRUB manually or by using the Ubuntu Live CD.

I tried the Live CD first. All the instructions say to boot to the CD, open a terminal, and enter: sudo grub
I get an error message: command not found.

Then I tried the manual method, which (after mounting the relevant partition) includes the instructions:

Reinstall the boot manager by typing "sudo grub-install --root-directory=/mnt/ /dev/sdX", replacing "X" with the Ubuntu drive's letter, and then hitting "Enter." For example, "/dev/sda" is the Ubuntu drive for most users.

[This step appeared to work fine.]

Then: Restart the computer into your Ubuntu system.

Alas, the computer restarts to sh:grub and I don't know how to get from there to either Linux or Windows, or what to do to fix this problem. At this point I have no working system on that computer. Fortunately I have another computer so I can get onto the Web and ask for help!

Can anyone help me sort this out? As a last resort I could reinstall Ubuntu but I really would prefer not to have to do that. Besides, it annoys me greatly that Windows destroys or disables GRUB and I want to conquer the problem!

Thanks for any help you can give me. --Jean

---

### Post by wilee-nilee on 2010-11-10
Your close;) post the bootscript in my signature in code tags. To get the code tags the easiest way is to paste the text in a reply then highlight it then click on the # in the reply panel. It is a lot of text so the tags are important for ease of reading

---

### Post by avalook on 2010-11-10
Here is the output from boot_info_script. Thanks for any insight you can give me.
--Jean

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,800,325   190,282,746   159,482,422   7 HPFS/NTFS
/dev/sda4         190,289,925   976,768,064   786,478,140   5 Extended
/dev/sda5         976,414,698   976,768,064       353,367  82 Linux swap / Solaris
/dev/sda6         190,290,051   976,414,634   786,124,584  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        1A0AF8100AF7E723                       ntfs       RECOVERY                      
/dev/sda3        9EE2FA2AE2FA05F5                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c49df37c-98d4-45eb-9bc2-84ec1235491c   swap                                     
/dev/sda6        7492729b-24f3-479d-b8a9-95f3ae2167ec   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7492729b-24f3-479d-b8a9-95f3ae2167ec

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

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.32-25-generic
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.10, kernel 2.6.32-24-generic
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-24-generic (recovery mode)
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.10, kernel 2.6.32-23-generic
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-23-generic (recovery mode)
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.10, kernel 2.6.32-22-generic
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-22-generic (recovery mode)
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.10, kernel 2.6.28-16-generic
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 10.10, kernel 2.6.28-16-generic (recovery mode)
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Chainload into GRUB 2
root		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7492729b-24f3-479d-b8a9-95f3ae2167ec
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=7492729b-24f3-479d-b8a9-95f3ae2167ec /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c49df37c-98d4-45eb-9bc2-84ec1235491c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 112.7GB: boot/grub/core.img
 112.6GB: boot/grub/menu.lst
 112.6GB: boot/grub/stage2
 112.6GB: boot/initrd.img-2.6.28-16-generic
 112.6GB: boot/initrd.img-2.6.32-22-generic
 112.6GB: boot/initrd.img-2.6.32-23-generic
 112.6GB: boot/initrd.img-2.6.32-24-generic
 112.6GB: boot/initrd.img-2.6.32-25-generic
 112.6GB: boot/initrd.img-2.6.35-22-generic
 112.6GB: boot/vmlinuz-2.6.28-16-generic
 112.6GB: boot/vmlinuz-2.6.32-22-generic
 112.6GB: boot/vmlinuz-2.6.32-23-generic
 112.6GB: boot/vmlinuz-2.6.32-24-generic
 112.6GB: boot/vmlinuz-2.6.32-25-generic
 112.6GB: boot/vmlinuz-2.6.35-22-generic
 112.6GB: initrd.img
 112.6GB: initrd.img.old
 112.6GB: vmlinuz
 112.6GB: vmlinuz.old

```

---

### Post by wilee-nilee on 2010-11-10
Run these commands from the booted live Ubuntu cd.
```
sudo mount /dev/sda6 /mnt
```
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot to the Ubuntu install and then run.
```
sudo update-grub
```

These commands are from this link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by avalook on 2010-11-10
I did the first two steps. When I reboot, all I get is 
```
sh: GRUB
```

I can't get into Ubuntu (or Windows) to do the third step or anything else.

---

### Post by Rubi1200 on 2010-11-10
For some reason you have legacy-GRUB installed on sda6:
```
Boot files/dirs:  [COLOR=Red] /boot/grub/menu.lst[/COLOR] /etc/fstab /boot/grub/core.img


```In this case, I do not think a simple reinstall will work.

Rather, you need to purge and then reinstall GRUB using the chroot method outlined here:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

However, I prefer you wait for input from wilee-nilee before proceeding.

Thanks.

---

### Post by wilee-nilee on 2010-11-10
I think it is the dell data safe program I noticed that it was a dell. I missed that part in the script.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)
**Disregard the dell data safe.**

So to this we have to reload the W7 bootloader if you don't have a W7 recovery disc you can use this one, or a install disc.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Here are the instructions to getting to the command terminal in W7 on the booted recovery or install disc. Just run the one command. Boot into W7 and look for the dell program I think it is in the remove programs in control. Notice the link at the bottom of the W7 forums it is a good visual aid.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
```
BootRec.exe /fixmbr
```  
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by wilee-nilee on 2010-11-10
> **Rubi1200 said:**
> For some reason you have legacy-GRUB installed on sda6:
```
Boot files/dirs:  [COLOR=Red] /boot/grub/menu.lst[/COLOR] /etc/fstab /boot/grub/core.img


```In this case, I do not think a simple reinstall will work.

Rather, you need to purge and then reinstall GRUB using the chroot method outlined here:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

However, I prefer you wait for input from wilee-nilee before proceeding.

Thanks.

No man you are correct OP you can reload the W7 as suggested if you really need it now. I am not real familiar of what to do when grub-legacy and grub2 is mixed together.

Running the command with the W7 will reload the mbr and you will have W7 back for the moment. This is fixable but needs somebody who knows how.

**Edit in my haste to stop my mistake which shouldn't cause any problems I missed rubi1200 advice they know this stuff I would follow them if was me.**

---

### Post by avalook on 2010-11-10
Do you think I should I try to fix the Windows MBR first, or purge and then reinstall GRUB first? 

I don't need Windows immediately. I can use my other Ubuntu computer for a few days, if necessary. --Jean

---

### Post by Quackers on 2010-11-10
It is possible that if you follow Rubi1200's link to drs305's guide for purging and re-installing grub, Windows 7 may boot from the grub menu. W7 seems to be more robust than Vista or XP were.

---

### Post by wilee-nilee on 2010-11-10
> **avalook said:**
> Do you think I should I try to fix the Windows MBR first, or purge and then reinstall GRUB first? 

I don't need Windows immediately. I can use my other Ubuntu computer for a few days, if necessary. --Jean

I only suggested not realizing rubi1200 solution, don't worry about reloading the W7 bootloader, just ask any questions, rubi1200 will help. There are others on line who caught this thankfully as well.

---

### Post by avalook on 2010-11-10
Rubi1200's instructions got GRUB back, and I just booted successfully into Ubuntu. :D

Now trying boot to Windows... YES! That's working too. :D

Thank you, thank you, all! What a great resource this forum is. I rarely need to ask a question, but when I do, you guys & gals always come through for me.

Now to remember how to mark this [Solved].
--Jean

---

### Post by Quackers on 2010-11-10
> **avalook said:**
> Now to remember how to mark this [Solved].
--Jean

Thread tools near the top of the page.

I like a happy ending :-)

---

### Post by Rubi1200 on 2010-11-10
> **Quackers said:**
> I like a happy ending :-)
Me too :)

@ avalook: glad things are sorted out now for you!

Enjoy :)

---

### Post by wilee-nilee on 2010-11-10
Me To!!!!!!!!!!! I knew you were in good hands and drs305 tutorials are really well crafted and understandable.

---

