---
title: "drive won't boot after installing Koala 9.10 next to windows 2000"
date: 2010-04-23
forum: General Help
---

### Post by zamek on 2010-04-23
I installed karmic koala 9.10 via the wubi installer in a separate partition with windows 2000 being the original operating system. Now nothing boots. I use to get a 'missing ntldr' message but lately I just get a grub loading error: 'no such partition' then a 'grub rescue>' prompt and nothing else. I've tried the numerous help pages in order to see what is wrong but always get stuck when something they say to do doesn't work for me and then I don't know what to do next. I can run koala from the installation cd and can see the contents of both the linux and windows partitions. The grub folder is there too but I haven't been able to reinstall it with the methods suggested in []("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") or the numerous other help pages I've looked at. Can anyone tell me what I should be doing to get this drive to boot? I'm far from an expert on all this so if you think you can help please don't assume that I can follow general instructions as I'm still at the stage that I require all the specifics details on *how* it should be done especially with command lines instructions. Thanks

---

### Post by inputpower on 2010-04-23
Does your computer still boot to Windows 2000. If so I would run Spinrite or do a check disk to check the HDD, the drive my be dying on you. That would be a good place to start if windows boots. If you have not saved any information on your Ubuntu installation you may consider just reinstalling. A new partition with a clean install of Ubuntu would be nice.
-good luck

---

### Post by oldfred on 2010-04-23
This is often the fix for wubi in 9.10

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by zamek on 2010-04-23
no windows doesn't boot, it just stops at the 'grub rescue>' prompt. I have reinstalled Koala twice but it hasn't helped.

---

### Post by zamek on 2010-04-23
how do I follow this solution [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10") since I can't boot into windows?

---

### Post by zamek on 2010-04-23
this is the result of the info script I finallly managed to get

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b580b57

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   323,902,529   323,902,467   7 HPFS/NTFS
/dev/sda2         323,902,530   398,283,479    74,380,950   5 Extended
/dev/sda5    *    323,902,593   396,066,509    72,163,917  83 Linux
/dev/sda6         396,066,573   398,283,479     2,216,907  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        F62C37CA2C378521                       ntfs                                     
/dev/sda5        5f2da811-2317-4a01-ab52-19e95049db65   ext3                                     
/dev/sda6        39b73e93-0ec2-4d21-ae05-2768d40f2e43   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/F62C37CA2C378521  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr = "Ubuntu"
######
=========================== sda5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 5f2da811-2317-4a01-ab52-19e95049db65
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 5f2da811-2317-4a01-ab52-19e95049db65
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5f2da811-2317-4a01-ab52-19e95049db65 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 5f2da811-2317-4a01-ab52-19e95049db65
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5f2da811-2317-4a01-ab52-19e95049db65 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f62c37ca2c378521
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=5f2da811-2317-4a01-ab52-19e95049db65 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=39b73e93-0ec2-4d21-ae05-2768d40f2e43 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 188.5GB: boot/grub/core.img
 188.6GB: boot/grub/grub.cfg
 188.5GB: boot/initrd.img-2.6.31-14-generic
 188.6GB: boot/vmlinuz-2.6.31-14-generic
 188.5GB: initrd.img
 188.6GB: vmlinuz

---

### Post by zamek on 2010-04-23
I also managed to download and install the wubildr patch and will now reboot to see if it works

---

### Post by zamek on 2010-04-23
same problem as before: booting stops at 'grub rescue>' prompt

---

### Post by oldfred on 2010-04-23
I do not have wubi so I do not know if this is correct but you have two sets of wubi files one in root and one in a subdirectory. Did you fix both or you problem my be that you have two versions.

Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /[COLOR=DarkRed]wubildr.mbr [/COLOR]
                       /ubuntu/winboot/[COLOR=DarkRed]wubildr.mbr[/COLOR] /wubildr 
                       /ubuntu/winboot/wubildr

---

### Post by zamek on 2010-04-23
Since I can boot into koala via the wubi installer disk I applied the wubilder solution given at [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10"). Instead of just replacing the existing wubildr I first renamed it to wubildrbad before copying the new wubildr to that location on the c:\ drive. Should I have overwritten the old wubildr file like the instructions say instead of renaming it first? Could that cause it not to function properly? I didn't know I had more than one wubildr. Is there suppose to be more than one? If not should I delete one and which one should go? And how do you delete it properly so that associated files still work? What is the wubilr.mdr file? 

I also tried the solution given at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Recovery Using the Ubuntu Desktop/Live CD (RECOMMENDED)]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Recovery Using the Ubuntu Desktop/Live CD (RECOMMENDED)") and when I tried to reboot it stopped at the 'sh:grub'  prompt instead of the 'grubrescue >' promt. After that I tried the repair method suggested on this page [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html") but this just got me back the 'grub rescue>' prompt.

why is that I seem to be able to save to the c:/drive while I'm in linux (saved the wubilder file) but the stuff I save in my linux partition disappears after rebooting from the wubi cd?

Also does anyone know why I couldn't open the RESULTS.txt or boot.ini files with gedit? The error says 'gedit has not been able to detect the character coding'. The default coding is western iso 8859-15 and the other codes I tried didn't work any better. I managed to see results.txt with openoffice wordprocessor but couldn't do that with boot.ini: Is there a reason why the boot.ini says to boot windows xp yet I know that the os on the hard drive is windows 2000? Is this a potential problem? On another help page [http://oreilly.com/pub/h/2337]("http://oreilly.com/pub/h/2337") I found that windows 2000 should be written in the boot.ini file as 

[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000"

and not as it is now:

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

should I edit this line to see if windows will then boot? unfortunately I don't have the windows 2000 disk anymore so that makes repairing the windows section more difficult.

---

### Post by oldfred on 2010-04-23
With wubi you do not have a standard dual boot. You should not follow any of the instructions for installing grub or grub2 to the MBR. Wubi boots thru windows so you need windows in the MBR to be able to boot. The the wubi.mbr takes over and you boot into grub and have a full ubuntu install like a normal install but running inside the windows NTFS partition. It is intended for extended testing and allows updating that the liveCD does not. If then you like Ubuntu it is assumed you will do a regular full install into separate partitions and using grub as the boot loader.

Make sure you have the windows boot loader in the MBR.  windows fixmbr command. IF you ran the fixboot you may have overwritten the boot.ini that also had a line to boot Ubuntu?

---

### Post by zamek on 2010-04-23
so what should I do? if I remove wubi and install the regular ubuntu will that fix things? I 'm beginning to doubt it...especially that I can't boot into windows anymore.

---

### Post by oldfred on 2010-04-23
this has instructions on reinstalling the windows boot loader.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You can also install a generic windows boot loader from Ubuntu, you may have to enable universe repository:

Restore basic windows boot loader
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

