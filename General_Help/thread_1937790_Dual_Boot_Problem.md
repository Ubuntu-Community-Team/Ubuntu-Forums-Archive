---
title: "Dual Boot Problem"
date: 2012-03-08
forum: General Help
---

### Post by cssutto on 2012-03-08
I decided to make more room on my hard drive and screwed up.

When attempting to load Windows XP, I get the error message "missing NTLDR".

I deleted the directory "Preload" from my desktop.  I suspect that is the problem.

I remember deleting it once before with no problem.

I am running l0.4 and windoze.

Is there a way to get NTLDR back without the original XP installation disk?  This machine came pre-loaded and without an installation disk.

I do have a complete backup on an external drive, but can not find a Preload directory on it.



The backup was made with rsync and has saved me many times before, but not this time, at least so far.

Any suggestions?

---

### Post by gadolinio on 2012-03-08
I don't think that file is in a directory located in your desktop. As far as I remember, the NTLDR file is in the C drive. Look for it in your backup

---

### Post by lindsay7 on 2012-03-08
this may help you.

[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by cssutto on 2012-03-08
> **lindsay7 said:**
> this may help you.

[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

Got it and went through the process.

It loads ubuntu as it should but there is no Windows on the boot menu.

It removed the grub menu from its previous location and now I can not find the grub menu to add windows to the list.

Will it work if I edit grub in the boot list window to list Microsoft Windows XP Professional?

If not, where might I look for the grub menu?

I have the old menu on my backup so I know how to edit it to show
 title		Microsoft Windows XP Professional

---

### Post by dave2001 on 2012-03-08
The "missing NTLDR" message is telling you some of the boot-files needed to launch windows are missing or corrupted. These files are not always kept on the same partition as the windows installation. The earlier posted boot-repair application looks grub-based to me, and it may not have the needed tools to fix a fubar'd windows boot-loader.

You could try this application, called Easy BCD, which rebuilds the windows boot-loader, and will allow you to customize it so it will also launch Ubuntu (just install grub on the same partition as Ubuntu). 

[http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html](http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html)

---

### Post by cssutto on 2012-03-09
> **dave2001 said:**
> The "missing NTLDR" message is telling you some of the boot-files needed to launch windows are missing or corrupted. These files are not always kept on the same partition as the windows installation. The earlier posted boot-repair application looks grub-based to me, and it may not have the needed tools to fix a fubar'd windows boot-loader.

You could try this application, called Easy BCD, which rebuilds the windows boot-loader, and will allow you to customize it so it will also launch Ubuntu (just install grub on the same partition as Ubuntu). 

[http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html](http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html)


I looked at that and all I see is Vista, Vista, Vista.

I see no reference to its working with XP

---

### Post by Mark Phelps on 2012-03-09
Sigh ... once again, BAD info about EasyBCD ...

That app works with the BOOTMGR present in Vista and Win7; it does not work with the NTLDR present in XP.

What you could try (since you don't have an XP disk), is to download and burn an ISO of the Boot-Repair CD, boot from that, and see if that can repair your XP boot:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by cssutto on 2012-03-09
> **Mark Phelps said:**
> Sigh ... once again, BAD info about EasyBCD ...

That app works with the BOOTMGR present in Vista and Win7; it does not work with the NTLDR present in XP.

What you could try (since you don't have an XP disk), is to download and burn an ISO of the Boot-Repair CD, boot from that, and see if that can repair your XP boot:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")


Thank you.

As stated earlier, I have installed and run boot repair.

However it removed windoze from my grub menu and I can not find where the new menu list is located and therefore I can not add windoze to the list.

---

### Post by dave2001 on 2012-03-09
Apologies if I pointed in a bad direction. I've used EasyBCD with Win7 on a machine which ALSO had WinXP. I wasn't thinking about if it would work on a machine with ONLY winXP.

On a another note, if you can borrow it from someone else, I think anyone's XP install disc should work for a repair. 

Also, all pre-loaded windows systems I've ever encountered come with the installation CD information *somewhere*. Sometimes it's in a seperate "recovery" partition, and I've also seen it kept in a file on the c partition with Windows. On windowsXP machines that folder is usually called i386. This information can be converted into a CD.

---

### Post by LostFarmer on 2012-03-09
Download boot-info-script , read the ho-to-use first. and post the RESULTS.txt 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by cssutto on 2012-03-09
OK, here are the results.

It is appears that I have some disk errors, which I have suspected for some time but don't know how to fix them.

I should be fair and confess that I am seriously considering purchasing a new HP laptop with windoze 7 installed and installing linux over it.

This machine was top of the line 4 or 5 years ago, but I would like better video and graphics capability.

And it would make solving this problem easy.

                  ```
Boot Info Script 0.60    from 17 May 2011


#============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 9 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda1 has 
                       76244416 sectors, but according to the info from 
                       fdisk, it has 76250096 sectors.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 6.06.2 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda9 and looks at sector 111951888 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 6.06.1 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    76,250,159    76,250,097   7 NTFS / exFAT / HPFS
/dev/sda2          76,250,160    85,715,279     9,465,120   b W95 FAT32
/dev/sda3          85,722,839   162,336,824    76,613,986   f W95 Extended (LBA)
/dev/sda5          85,722,840    86,638,544       915,705  83 Linux
/dev/sda6         159,220,278   162,336,824     3,116,547  82 Linux swap / Solaris
/dev/sda7    *    120,840,993   157,581,584    36,740,592  83 Linux
/dev/sda8         157,581,648   159,220,214     1,638,567  82 Linux swap / Solaris
/dev/sda9          86,638,608   119,314,754    32,676,147  83 Linux
/dev/sda10        119,314,818   120,840,929     1,526,112  82 Linux swap / Solaris
/dev/sda4         162,336,825   234,436,544    72,099,720  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5868D0EE68D0CBBE                       ntfs       Preload
/dev/sda10       fc004341-3b2d-48a3-8fa9-54bf631fd151   swap       
/dev/sda2        8ED2-682C                              vfat       
/dev/sda4        bf19695c-44a5-4697-80a3-31ca7bec0756   ext3       
/dev/sda5        cd175789-09b6-4c96-a90b-1f04c4dd98a3   ext3       
/dev/sda6        9005afcb-d9c8-4677-90f0-ebcc25bd1487   swap       
/dev/sda7        059226fd-c744-4b50-9994-5b44ae564fa6   ext3       
/dev/sda8        a6d0483f-ab45-43ce-9ff6-f45d5b2ae6a5   swap       
/dev/sda9        6a294583-3a88-4504-a661-ee5658c80919   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/Preload           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda9        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title        Ubuntu, kernel 2.6.15-29-686
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.15-29-686 root=/dev/sda7 ro quiet splash
initrd        /boot/initrd.img-2.6.15-29-686
savedefault
boot

title        Ubuntu, kernel 2.6.15-29-686 (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.15-29-686 root=/dev/sda7 ro single
initrd        /boot/initrd.img-2.6.15-29-686
boot

title        Ubuntu, kernel 2.6.15-29-386
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.15-29-386 root=/dev/sda7 ro quiet splash
initrd        /boot/initrd.img-2.6.15-29-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.15-29-386 root=/dev/sda7 ro single
initrd        /boot/initrd.img-2.6.15-29-386
boot

title        Ubuntu, memtest86+
root        (hd0,6)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title        Ubuntu, kernel 2.6.15-26-386 (on /dev/sda4)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/sda4 ro quiet splash 
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title        Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/sda4)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/sda4 ro single 
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda4.
title        Ubuntu, memtest86+ (on /dev/sda4)
root        (hd0,3)
kernel        /boot/memtest86+.bin  
savedefault
boot

--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

 none /proc/bus/usb usbfs defaults  0  0

proc /proc proc defaults 0 0
/dev/sda7 / ext3 defaults,errors=remount-ro 0 1
/dev/sda8 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/Preload ntfs umask=222,utf8 0 0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  63.793480396 = 68.497728000   boot/grub/menu.lst                             1
  63.863766193 = 68.573196800   boot/grub/stage2                               2
  63.761559010 = 68.463452672   boot/initrd.img-2.6.15-29-386                  8
  63.831341267 = 68.538380800   boot/initrd.img-2.6.15-29-686                  4
  63.812706470 = 68.518371840   boot/vmlinuz-2.6.15-29-386                     2
  63.815136433 = 68.520980992   boot/vmlinuz-2.6.15-29-686                     2

=========================== sda9/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,9)'
search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-40-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-40-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-40-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-40-generic ...'
    linux    /boot/vmlinuz-2.6.32-40-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-40-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-39-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-39-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-39-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-39-generic ...'
    linux    /boot/vmlinuz-2.6.32-39-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-39-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-38-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-38-generic ...'
    linux    /boot/vmlinuz-2.6.32-38-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-37-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-37-generic ...'
    linux    /boot/vmlinuz-2.6.32-37-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-36-generic ...'
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-35-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-35-generic ...'
    linux    /boot/vmlinuz-2.6.32-35-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6a294583-3a88-4504-a661-ee5658c80919 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 6a294583-3a88-4504-a661-ee5658c80919
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, kernel 2.6.15-26-386 (on /dev/sda4)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set bf19695c-44a5-4697-80a3-31ca7bec0756
    linux /boot/vmlinuz-2.6.15-26-386 root=/dev/sda4 ro quiet splash
    initrd /boot/initrd.img-2.6.15-26-386
}
menuentry "Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/sda4)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set bf19695c-44a5-4697-80a3-31ca7bec0756
    linux /boot/vmlinuz-2.6.15-26-386 root=/dev/sda4 ro single
    initrd /boot/initrd.img-2.6.15-26-386
}
menuentry "Ubuntu, memtest86+ (on /dev/sda4)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set bf19695c-44a5-4697-80a3-31ca7bec0756
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, kernel 2.6.15-29-686 (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 059226fd-c744-4b50-9994-5b44ae564fa6
    linux /boot/vmlinuz-2.6.15-29-686 root=/dev/sda7 ro quiet splash
    initrd /boot/initrd.img-2.6.15-29-686
}
menuentry "Ubuntu, kernel 2.6.15-29-686 (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 059226fd-c744-4b50-9994-5b44ae564fa6
    linux /boot/vmlinuz-2.6.15-29-686 root=/dev/sda7 ro single
    initrd /boot/initrd.img-2.6.15-29-686
}
menuentry "Ubuntu, kernel 2.6.15-29-386 (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 059226fd-c744-4b50-9994-5b44ae564fa6
    linux /boot/vmlinuz-2.6.15-29-386 root=/dev/sda7 ro quiet splash
    initrd /boot/initrd.img-2.6.15-29-386
}
menuentry "Ubuntu, kernel 2.6.15-29-386 (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 059226fd-c744-4b50-9994-5b44ae564fa6
    linux /boot/vmlinuz-2.6.15-29-386 root=/dev/sda7 ro single
    initrd /boot/initrd.img-2.6.15-29-386
}
menuentry "Ubuntu, memtest86+ (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 059226fd-c744-4b50-9994-5b44ae564fa6
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda9 :
UUID=6a294583-3a88-4504-a661-ee5658c80919 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda10 :
UUID=fc004341-3b2d-48a3-8fa9-54bf631fd151 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/Preload ntfs-3g defaults,locale=en_US.UTF-8 0 0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  53.866554260 = 57.838772224   boot/grub/grub.cfg                             1
  53.321247101 = 57.253253120   boot/initrd.img-2.6.32-24-generic              4
  53.398345947 = 57.336037376   boot/initrd.img-2.6.32-25-generic              3
  53.342914581 = 57.276518400   boot/initrd.img-2.6.32-26-generic              5
  53.359287262 = 57.294098432   boot/initrd.img-2.6.32-27-generic              3
  53.351543427 = 57.285783552   boot/initrd.img-2.6.32-28-generic              5
  53.424507141 = 57.364127744   boot/initrd.img-2.6.32-29-generic              8
  53.432212830 = 57.372401664   boot/initrd.img-2.6.32-30-generic              7
  45.236179352 = 48.571977728   boot/initrd.img-2.6.32-31-generic              4
  45.160091400 = 48.490278912   boot/initrd.img-2.6.32-32-generic             11
  54.451076508 = 58.466398208   boot/initrd.img-2.6.32-33-generic             152
  45.571804047 = 48.932352000   boot/initrd.img-2.6.32-34-generic             83
  45.131980896 = 48.460095488   boot/initrd.img-2.6.32-35-generic              4
  46.027366638 = 49.421508608   boot/initrd.img-2.6.32-36-generic             28
  46.034824371 = 49.429516288   boot/initrd.img-2.6.32-37-generic             101
  47.136341095 = 50.612260864   boot/initrd.img-2.6.32-38-generic             67
  47.113212585 = 50.587426816   boot/initrd.img-2.6.32-39-generic             25
  48.992179871 = 52.604952576   boot/initrd.img-2.6.32-40-generic             19
  53.402236938 = 57.340215296   boot/vmlinuz-2.6.32-24-generic                 4
  53.327018738 = 57.259450368   boot/vmlinuz-2.6.32-25-generic                 2
  53.408760071 = 57.347219456   boot/vmlinuz-2.6.32-26-generic                 3
  53.386604309 = 57.323429888   boot/vmlinuz-2.6.32-27-generic                 2
  53.331600189 = 57.264369664   boot/vmlinuz-2.6.32-28-generic                 5
  53.416011810 = 57.355005952   boot/vmlinuz-2.6.32-29-generic                 3
  53.378791809 = 57.315041280   boot/vmlinuz-2.6.32-30-generic                 2
  53.436012268 = 57.376481280   boot/vmlinuz-2.6.32-31-generic                 3
  45.152667999 = 48.482308096   boot/vmlinuz-2.6.32-32-generic                 6
  46.346031189 = 49.763672064   boot/vmlinuz-2.6.32-33-generic                 2
  54.369747162 = 58.379071488   boot/vmlinuz-2.6.32-34-generic                27
  45.426853180 = 48.776712192   boot/vmlinuz-2.6.32-35-generic                38
  45.138904572 = 48.467529728   boot/vmlinuz-2.6.32-36-generic                20
  45.574127197 = 48.934846464   boot/vmlinuz-2.6.32-37-generic                51
  46.939682007 = 50.401099776   boot/vmlinuz-2.6.32-38-generic                45
  54.254932404 = 58.255790080   boot/vmlinuz-2.6.32-39-generic                44
  45.612113953 = 48.975634432   boot/vmlinuz-2.6.32-40-generic                70
  48.992179871 = 52.604952576   initrd.img                                    19
  47.113212585 = 50.587426816   initrd.img.old                                25
  45.612113953 = 48.975634432   vmlinuz                                       70
  54.254932404 = 58.255790080   vmlinuz.old                                   44

=========================== sda4/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/sda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/sda4 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/sda4 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

title        Ubuntu, memtest86+
root        (hd0,3)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP
root        (hd0,1)
savedefault
makeactive
chainloader    +1

--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  85.150425434 = 91.429573120   boot/grub/menu.lst                             1
  85.080208302 = 91.354178048   boot/grub/stage2                               2
  85.117893696 = 91.394642432   boot/initrd.img-2.6.15-26-386                  3
  85.143764973 = 91.422421504   boot/vmlinuz-2.6.15-26-386                     2
  85.117893696 = 91.394642432   initrd.img                                     3
  85.143764973 = 91.422421504   vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda5

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200

Unknown BootLoader on sda7

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb
```

---

### Post by oldfred on 2012-03-09
All Windows NTFS partition have to have NTFS signatures which includes start & size info identical to the partition table and which boot loader to use.

You also have two boot flags. Grub does not use boot flag, but Windows has to have one to boot (not necessary with grub), repair or install. In Windows that is the active partition.

Delete boot flag from sda7, but leave the one on sda1, so you can use your XP install disk to run repairs including fixBoot & chkdsk. Not sure if your other boot files are missing? If so you must have deleted another Windows partition that had the boot files. 

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by cssutto on 2012-03-10
The CD Rom mount point, etc., is included in the directory <Media> which I deleted.

Also all windoze files which I found out when I looked at GParted.

The entire ntfs partition is empty, which means also that all windoze files are gone.

So I could not even use the Ubuntu starter disk if I had it.

Actually I downloaded a copy and found out the CD drive would not work when I tried to burn it.

Now I can't find a source from which to purchase a 10.4 DVD.  All I can find are either server or the latest version.

Can someone point me to a source?

Or is there another way to fix it?

CSSJR

---

### Post by cssutto on 2012-03-10
I was going in circles when I posted the above.

I fixed the cd mount point so wait until I burn it before we go any farther.

---

### Post by cssutto on 2012-03-11
I am going to purchase a new computer.

A HP Pavillion with everything on it.

Thanks for the help, but time to quit messing with a dead horse.

---

