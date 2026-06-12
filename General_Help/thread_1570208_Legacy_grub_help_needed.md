---
title: "Legacy grub help needed"
date: 2010-09-07
forum: General Help
---

### Post by quadproc on 2010-09-07
I hope that someone who understands legacy grub can answer a question for me.

I borked this system by deleting a partition; this caused my partition numbers to change but grub doesn't know about the change so it is looking in the wrong place for the stage 2 file.  I get error 17 when I try to boot from the usual disk (thank goodness for USB drives!).

Here is a bit more of the history: I had two Ubuntu versions on the main disk, each living in its own pair of Linux/swap partitions.  The older system was in partition 5 and its swap was in 6; the newer system was in partition 7 and its swap in 8.  There was no reason to have two swap partitions so I decided to delete what used to be partition 6 and to use a single swap partition whose number used to be 8.  Thus, I now have partitions 5, 6, and 7 being old system, new system, and swap.  All this was done in preparation for installing a newer Ubuntu version in a not-yet-created partition.

I ran the bootinfo script and learned that grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.  Obviously, this is now a problem because partition #7 is a swap partition.

I was running grub 0.97 because I upgraded from 9.04 to 9.10 and I would rather prefer to keep that grub if I could.  I have a CDROM which contains grub 0.97.

I have looked in my /boot/grub directory and I cannot find any file entries that refer to sda7, (0,6), or anything like that so I think that I must not be looking in the right place.  I think that I would rather use a UUID than a partition number.

Could someone point me to the place where I need to repair grub's idea of the partition number, or perhaps suggest a more automated way to let the system figure out what belongs where?  Thanks.

quadproc

---

### Post by andrewthomas on 2010-09-07
[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

this should do you right

---

### Post by oldfred on 2010-09-08
fstab should be using UUIDs and be ok, although the comment on being in sda8 during install will now be wrong. 

But if something else changed or you are not using UUIDs, you may have to update fstab also.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by confused57 on 2010-09-08
What you can try is at the initial grub boot menu, highlight your 1st Ubuntu entry, press "e" to edit, change root from (hd0,7) to (hd0,6), then "b" to boot.  Then make it permanent in your menu.lst, if it works.

---

### Post by quadproc on 2010-09-08
andrewthomas: Thanks for the link.  I read that page and tried to do a manual grub install but ran into a problem.  When I ran grub, I told it root (hd0,5) [this is where my latest Ubuntu system lives] and received an acknowledgement about the kind of file system.  Then I told it setup (hd0) and received a couple of lines saying that it was checking if "/boot/grub/stage1" exists  no and checking if "/grub/stage1" exists  no.  Then it reported error 2.  So it appears that it can't see these files on /dev/sda5.  Yet, I can temporarily mount /dev/sda5 while running from a Live CD copy on a USB stick and I find the /boot/grub directory with a bunch of files including stage1, stage2, and a bunch of stage1_5 files.  So now I am perplexed.  When I do a file stage* I get:
stage1: x86 boot sector; GRand Unified Bootloader, stage1 version 0x3, code offset 0x48
stage2: GRand Unified Bootloader stage2 version 3.2, identifier 0x0, GRUB version 0.97, configuration file /boot/grub/menu.lst
which looks valid to me.

oldfred: Yes, I knew about the fstab change requirement and I had done that; I just didn't mention it in my original posting.  I figured that, even if the swap specification was wrong that the system would still run but without swap being enabled, but I changed the file in the same session as the one where I used gparted to move around partitions.

confused57: Unfortunately, I don't get an initial grub menu when I try to boot - the system just displays grub error 17.

Can anyone shed light on my situation?  I believe that somehow I need to change the partition number that is reported in the boot info script for where the system is looking; presumably this is done by grub's setup command, but for some reason grub doesn't see the files it wants so it errors while trying to do this.

quadproc

---

### Post by oldfred on 2010-09-08
This will tell us all about your system so we can make better choices of fixes.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by quadproc on 2010-09-08
> **oldfred said:**
> This will tell us all about your system so we can make better choices of fixes.
.
Well, OK, but the script output may be a bit confusing.  This system has had a lot of changes made to it over time and consequently things such as partitions are not organized in a simple manner.  Also, at one time this system had Windows on it (it came that way) so you will see references to it even though it is long gone.  At the present instant, sdh is a USB stick which is plugged in but not in use.

sda is the first disk and contains the OSes; sdb is not really in use at the present time, sdc is dedicated entirely as /home in a single primary partition.  Disks sda and sdb are identical types; they are not partitioned identically.

Edit: This probably does not matter, but all hard disks are SATA.

I intend to aboilish the ntfs partition at some point, but I first need to know if doing so will cause problems for my motherboard/BIOS: it is an ASUS P6T SE which doesn't have enough memory on board to run ExpressGate so the BIOS looks on the system disk for the ExpressGate files; it doesn't find them so it reports that the ExpressGate installation is incomplete.

The menu files contain some junk: when I upgraded Ubuntu 9.04 to 9.10, the upgrade caused the grub menu to have entries for each version but it named them all 9.10!  The 9.04 versions do not work, presumably because some files from 9.04 were overwritten by 9.10.  But I never bothered to remove their entries from the list, nor did I remove the older Linux kernel.

I used the bootinfoscript055 that I captured a while back.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdh1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdh1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   284,655,734   284,653,687   7 HPFS/NTFS
/dev/sda2         284,655,735 1,953,520,064 1,668,864,330   5 Extended
/dev/sda5         284,655,798   636,222,194   351,566,397  83 Linux
/dev/sda6         636,222,258   888,121,394   251,899,137  83 Linux
/dev/sda7       1,927,928,583 1,953,520,064    25,591,482  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,629,762,119 1,629,762,057   5 Extended
/dev/sdb5                 126 1,233,695,609 1,233,695,484  83 Linux
/dev/sdb6       1,233,695,673 1,268,653,049    34,957,377  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   293,041,664   293,041,602  83 Linux


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 2000 MB, 2000682496 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *             63     3,903,794     3,903,732   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        26AE4A30AE49F937                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b92fb3a5-c503-4168-a61f-7e6ea6661a0a   ext3                                     
/dev/sda6        df533fe8-68c3-41f6-b030-e955feb580d9   ext3                                     
/dev/sda7        b071f4d5-5384-4267-9f78-99e163d6ea4a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        ae2cdad8-459c-4692-908d-eea07cd1fe9b   ext3                                     
/dev/sdb6        a7d2d1fc-dd54-4226-b4fd-f9c145f319a4   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        e61d892a-0341-4f99-a87b-c9345d9f9eb1   ext3                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdh1        2D6C-4B1E                              vfat       karmicUSB                     
/dev/sdh: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /y                       ext3       (rw)


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
# kopt=root=UUID=b92fb3a5-c503-4168-a61f-7e6ea6661a0a ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=b92fb3a5-c503-4168-a61f-7e6ea6661a0a

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

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        b92fb3a5-c503-4168-a61f-7e6ea6661a0a
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b92fb3a5-c503-4168-a61f-7e6ea6661a0a ro xforcevesa quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        b92fb3a5-c503-4168-a61f-7e6ea6661a0a
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b92fb3a5-c503-4168-a61f-7e6ea6661a0a ro xforcevesa  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        b92fb3a5-c503-4168-a61f-7e6ea6661a0a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b92fb3a5-c503-4168-a61f-7e6ea6661a0a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
# UUID=90658f08-20c1-487a-b584-331ee5cad324 none            swap    sw              0       0
# 9/6/10 substituted sda8 for swap
# /dev/sda8
UUID=b071f4d5-5384-4267-9f78-99e163d6ea4a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdg        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 147.0GB: boot/grub/menu.lst
 147.0GB: boot/grub/stage2
 147.0GB: boot/initrd.img-2.6.27-7-generic
 147.0GB: boot/vmlinuz-2.6.27-7-generic
 147.0GB: initrd.img
 147.0GB: vmlinuz

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=df533fe8-68c3-41f6-b030-e955feb580d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=df533fe8-68c3-41f6-b030-e955feb580d9

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
uuid        df533fe8-68c3-41f6-b030-e955feb580d9
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=df533fe8-68c3-41f6-b030-e955feb580d9 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        df533fe8-68c3-41f6-b030-e955feb580d9
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=df533fe8-68c3-41f6-b030-e955feb580d9 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.28-18-generic
uuid        df533fe8-68c3-41f6-b030-e955feb580d9
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=df533fe8-68c3-41f6-b030-e955feb580d9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-18-generic (recovery mode)
uuid        df533fe8-68c3-41f6-b030-e955feb580d9
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=df533fe8-68c3-41f6-b030-e955feb580d9 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.10, memtest86+
uuid        df533fe8-68c3-41f6-b030-e955feb580d9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Windows Vista/Longhorn (loader)
#root        (hd0,0)
#savedefault
#makeactive
#chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b92fb3a5-c503-4168-a61f-7e6ea6661a0a ro xforcevesa quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b92fb3a5-c503-4168-a61f-7e6ea6661a0a ro xforcevesa single 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=df533fe8-68c3-41f6-b030-e955feb580d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=b071f4d5-5384-4267-9f78-99e163d6ea4a none            swap    sw              0       0
#/dev/sdc1
UUID=e61d892a-0341-4f99-a87b-c9345d9f9eb1 /home        ext3    relatime,errors=remount-ro    0    2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdg        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


=================== sda6: Location of files loaded by Grub: ===================


 337.6GB: boot/grub/menu.lst
 337.9GB: boot/grub/stage2
 337.9GB: boot/initrd.img-2.6.28-18-generic
 337.9GB: boot/initrd.img-2.6.31-20-generic
 337.9GB: boot/vmlinuz-2.6.28-18-generic
 337.9GB: boot/vmlinuz-2.6.31-20-generic
 337.9GB: initrd.img
 337.9GB: initrd.img.old
 337.9GB: vmlinuz
 337.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 


```If you see anything that doesn't seem to make sense, then please ask.  I may be able to explain it.  Thanks.

quadproc

---

### Post by oldfred on 2010-09-08
It sounds like you tried to reinstall grub correctly, perhaps a typo on some line? (hd0,5) is sda6 where your 9.10 install now is.

Grub in the MBR is wrong as it is looking at sda7 which is now your swap, so you need to reinstall.

This looks like what your did.
#reset grub legacy boot
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or root (hd0,5)
setup (hd0)

You can try chrooting into sda6 and reinstalling grub legacy.

kansasnoob oneline chroot-----------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

kansasnoob's change sda6 to correct partition if needed:
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

#once chrooted:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

# uninstall both grub legacy & grub2 reinstall grub and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

---

### Post by quadproc on 2010-09-08
> **oldfred said:**
> It sounds like you tried to reinstall grub correctly, perhaps a typo on some line? (hd0,5) is sda6 where your 9.10 install now is.

Grub in the MBR is wrong as it is looking at sda7 which is now your swap, so you need to reinstall.

This looks like what your did.
#reset grub legacy boot
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or root (hd0,5)
setup (hd0)

Well, that is almost what I did.  What actually happened is that I tried to use grub's find command but every experience that I have with grub is that its find command never works - it always returns error 15 even when I use a full path name starting with /.  I knew from other sources that my desired OS was at (0,5) so I used that for the root command.  But then the setup command complained that it couldn't find the stage1 file.

> 
You can try chrooting into sda6 and reinstalling grub legacy.

kansasnoob oneline chroot-----------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

kansasnoob's change sda6 to correct partition if needed:
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

#once chrooted:
Here is where I get very apprehensive - I had a good running 9.10 setup and I don't want to damage it by installing updates, upgrades, etc.
> 
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
If I skip the above-quoted steps will there be risk?
> 
# uninstall both grub legacy & grub2 reinstall grub and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub grub-common
grub-install /dev/sda
grub-install --recheck /dev/sdaThanks for your help.

quadproc

---

### Post by confused57 on 2010-09-08
It may be beneficial to run a filesystem check on your Ubuntu partitions, instructions courtesy of forum member Herman:
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

---

### Post by quadproc on 2010-09-09
> **confused57 said:**
> It may be beneficial to run a filesystem check on your Ubuntu partitions, instructions courtesy of forum member Herman:

A good suggestion but the check did not find any problems and did not affect the grub error 17.

I have made some progress, though; I did manage to get some version of grub installed on the system so that the system can now boot from the first hard disk.  However, the only choices that I get on the grub menu are the old OS (8.10), the old OS in recovery mode, or memtest.  There is no mention of my newer OS.  So I need to figure out what to do to what files in order to add entries for my newer OS.

Once I get things working like they used to, I will post a summary of the procedure that finally worked for me. (done; please see post below)

quadproc

---

### Post by confused57 on 2010-09-09
You could try adding a configfile entry to your menu.lst to boot your other Ubuntu install:
[http://members.iinet.net.au/~herman546/p15.html#1._Configfile](http://members.iinet.net.au/~herman546/p15.html#1._Configfile)

---

### Post by quadproc on 2010-09-09
> **confused57 said:**
> You could try adding a configfile entry to your menu.lst to boot your other Ubuntu install:

Thanks for the suggestion.  I did that and now things seem to be working just like they used to, before I moved partitions around a few days ago.:D  To do the modifications to menu.lst, I copied out the relevant part of the /boot/grub.old/menu.lst that I had saved while trying to get grub to work.

For those who may be interested (and especially oldfred), here is what finally worked for me.  But before I describe that, I should say that I found a lot of things that do not work while I was searching the web about this problem.

I found a post from dranger003 dated July 25, 2006 that had some real insight and a procedure that almost worked.  I will list his procedure with my changes in red.

Running from a USB drive, in a terminal I started by making a clear place for the new grub files:
```

sudo mv /boot/grub /boot/grub.old
sudo mkdir /boot/grub

```Here is dranger003's code:
(my first intended partition is on [COLOR=Red]sda5[/COLOR])
```

sudo mount /dev/[COLOR=Red]sda5[/COLOR] /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
grub-install [COLOR=Red]--recheck[/COLOR] /dev/[COLOR=Red]sda[/COLOR]
[COLOR=Red]exit[/COLOR]

```You will need to umount everything that you mounted, above.

Before I added the --recheck to the grub-install command, I was getting errors that sda5 was not a block device or somesuch.

Thanks to all for your help, suggestions, insights, and knowledge.

quadproc

---

