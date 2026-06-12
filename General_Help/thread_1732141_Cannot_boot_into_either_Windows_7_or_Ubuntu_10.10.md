---
title: "Cannot boot into either Windows 7 or Ubuntu 10.10"
date: 2011-04-17
forum: General Help
---

### Post by jmvizanko on 2011-04-17
I have a Samsung RC512 laptop that came with Windows 7 installed.  I installed Ubuntu 10.10 using the automated repartitioning tool built into Ubuntu's installation.  Everything was going fine with selecting which OS to run in GRUB until today.  Not sure what happened, but the few out there guesses I have are, my fiance selected Windows Vista instead of 7 (no clue what that would do, and can you get it removed from the GRUB list?), the laptop went into hibernate (could this mess up GRUB?), or a windows update screwed with some crap (if only I didn't need windows for CAD, games, and Itunes....).

The problem is now that when I turn on my PC, I see the Samsung boot screen with F2 and F4 options, but then what happens next is my PC alternates between about 2 seconds of blank screen and 2 seconds of "-" in the top left corner ad infinitum.  Is this just a problem with GRUB?  And if so, how do I go about fixing it?  I don't even know which partitions do what on my computer (which means I probably don't even know enough to be dual booting).  Thanks for any help, as this is very unnerving, and I hope there is a solution that will work now and in any future similar event.

---

### Post by garvinrick4 on 2011-04-17
Windows Vista is the recovery partition for Windows 7, it is how grub reads that partition in
windows (not in grub-pc version 1.99~rcl).  No telling what happened after that or what commands it was told to do. 
Get your ubuntu install cd use try Ubuntu instead of install and when it boots up.
Open a terminal:
```
sudo fdisk -l
``` (lower case L) 
and lets see what is left on your hard drive:

---

### Post by jmvizanko on 2011-04-17
> **garvinrick4 said:**
> Windows Vista is the recovery partition for Windows 7, it is how grub reads that partition in
windows (not in grub-pc version 1.99~rcl).  No telling what happened after that or what commands it was told to do. 
Get your ubuntu install cd use try Ubuntu instead of install and when it boots up.
Open a terminal:
```
sudo fdisk -l
``` (lower case L) 
and lets see what is left on your hard drive:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbc7a5d4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       35390   284164096    7  HPFS/NTFS
/dev/sda3           35390       88412   425892865    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4           88412       91202    22411264   27  Unknown
/dev/sda5           35390       62727   219582157    7  HPFS/NTFS
/dev/sda6           62727       87647   200166400   83  Linux
/dev/sda7           87647       88412     6142976   82  Linux swap / Solaris

That's what I got.  Do you think the most likely problem was the "Vista" partition being selected?

---

### Post by garvinrick4 on 2011-04-17
Ok looks like you still got some Windows and some Linux and even a unknown.
Lets run a boot script only takes a minute. Go to the website I give you and DOWNLOAD
this script to your desktop in the Live CD you are using then run this code. Will put
a RESULTS.TXT on your desktop of your boot configuration. Copy and paste it to your
thread. We can fix from there. Good news is it looks like your Operating Systems are
still there now we can make bootable again.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by garvinrick4 on 2011-04-17
> That's what I got.  Do you think the most likely problem was the "Vista" partition being selected? We will never know what your fiance did or did not do, but it is done and behind and we all make mistakes. Let her off the hook and tell her it is OK. This is just the tip
of the Ice burg on your way through marriage bliss.

---

### Post by jmvizanko on 2011-04-18
> **garvinrick4 said:**
> We will never know what your fiance did or did not do, but it is done and behind and we all make mistakes. Let her off the hook and tell her it is OK. This is just the tip
of the Ice burg on your way through marriage bliss.

I'm not mad at her at all.  And I'll get the boot report to you this evening.

---

### Post by jmvizanko on 2011-04-18
> **garvinrick4 said:**
> Ok looks like you still got some Windows and some Linux and even a unknown.
Lets run a boot script only takes a minute. Go to the website I give you and DOWNLOAD
this script to your desktop in the Live CD you are using then run this code. Will put
a RESULTS.TXT on your desktop of your boot configuration. Copy and paste it to your
thread. We can fix from there. Good news is it looks like your Operating Systems are
still there now we can make bootable again.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   568,535,039   568,328,192   7 HPFS/NTFS
/dev/sda3         568,537,086 1,420,322,815   851,785,730   f W95 Ext d (LBA)
/dev/sda5         568,537,088 1,007,701,401   439,164,314   7 HPFS/NTFS
/dev/sda6       1,007,702,016 1,408,034,815   400,332,800  83 Linux
/dev/sda7       1,408,036,864 1,420,322,815    12,285,952  82 Linux swap / Solaris
/dev/sda4       1,420,322,816 1,465,145,343    44,822,528  27 Hidden HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        10E8F045E8F02A9C                       ntfs       SYSTEM                        
/dev/sda2        02B25A3FB25A377F                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        94EA790CEA78EBBC                       ntfs       SAMSUNG_REC                   
/dev/sda5        8C3C26BE3C26A2E6                       ntfs                                     
/dev/sda6        c8240ffd-b1b6-452a-85f8-f657fd196b9f   ext4                                     
/dev/sda7        76df3ee0-7083-45d6-b328-6f5175411180   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set c8240ffd-b1b6-452a-85f8-f657fd196b9f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set c8240ffd-b1b6-452a-85f8-f657fd196b9f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c8240ffd-b1b6-452a-85f8-f657fd196b9f
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=c8240ffd-b1b6-452a-85f8-f657fd196b9f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c8240ffd-b1b6-452a-85f8-f657fd196b9f
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=c8240ffd-b1b6-452a-85f8-f657fd196b9f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c8240ffd-b1b6-452a-85f8-f657fd196b9f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c8240ffd-b1b6-452a-85f8-f657fd196b9f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c8240ffd-b1b6-452a-85f8-f657fd196b9f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c8240ffd-b1b6-452a-85f8-f657fd196b9f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c8240ffd-b1b6-452a-85f8-f657fd196b9f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c8240ffd-b1b6-452a-85f8-f657fd196b9f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 10e8f045e8f02a9c
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 94ea790cea78ebbc
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=c8240ffd-b1b6-452a-85f8-f657fd196b9f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=76df3ee0-7083-45d6-b328-6f5175411180 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 601.9GB: boot/grub/core.img
 550.5GB: boot/grub/grub.cfg
 516.6GB: boot/initrd.img-2.6.35-22-generic
 517.9GB: boot/initrd.img-2.6.35-28-generic
 601.9GB: boot/vmlinuz-2.6.35-22-generic
 602.0GB: boot/vmlinuz-2.6.35-28-generic
 517.9GB: initrd.img
 516.6GB: initrd.img.old
 602.0GB: vmlinuz
 601.9GB: vmlinuz.old


That's what I got.  And once this is fixed (if we get there) is there a way to remove entries from the GRUB list?  And thanks again.

---

### Post by oldfred on 2011-04-18
I do not see anything in boot script that looks out of place. There are some programs in Win7 that have DRM and put data in the same place as some of grub2.

Have you just tried reinstalling grub2's boot loader to the MBR?

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda6 and want grub2 in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Two gui ways to modify grub menu:
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks-drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by jmvizanko on 2011-04-18
> **oldfred said:**
> I do not see anything in boot script that looks out of place. There are some programs in Win7 that have DRM and put data in the same place as some of grub2.

Have you just tried reinstalling grub2's boot loader to the MBR?

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda6 and want grub2 in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Two gui ways to modify grub menu:
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks-drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)


So here's what I tried:

ubuntu@ubuntu:~$ sudo mount/dev/sda6/mnt
sudo: mount/dev/sda6/mnt: command not found
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbc7a5d4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       35390   284164096    7  HPFS/NTFS
/dev/sda3           35390       88412   425892865    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4           88412       91202    22411264   27  Unknown
/dev/sda5           35390       62727   219582157    7  HPFS/NTFS
/dev/sda6           62727       87647   200166400   83  Linux
/dev/sda7           87647       88412     6142976   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

Is sda6 my Ubuntu partition, or is it sda3 or sda7?  Or did I do something wrong with the "sudo mount/dev/sda6/mnt" bit?

---

### Post by oldfred on 2011-04-18
You can copy & paste commands. It avoids the issues of some spaces not looking like spaces & 1 & l almost looking the same.

 sudo mount/dev/sda6/mnt

Mount is a command and then you have two parameters which have spaces between them. what I am mounting & where am I mounting it.

 ```
sudo mount /dev/sda6 /mnt
```

---

### Post by jmvizanko on 2011-04-18
> **oldfred said:**
> You can copy & paste commands. It avoids the issues of some spaces not looking like spaces & 1 & l almost looking the same.

 sudo mount/dev/sda6/mnt

Mount is a command and then you have two parameters which have spaces between them. what I am mounting & where am I mounting it.

 ```
sudo mount /dev/sda6 /mnt
```

Apparently I missed some spaces.  GRUB, Windows 7, and Ubuntu are all back up and running! :grin:  Thank you all for your help.

And thank you for the links to customize GRUB.  I will look into them, to make sure this never happens again (provided the vista selection is what happened, but then, I hated that unnecessarily long list anyway).

Although, if something like this does happen again, (was I right about windows updates or suspension of a particular laptop being another thing that could mess with GRUB?), would it hurt to just try the same thing again first?

---

### Post by oldfred on 2011-04-18
You can always reinstall grub2's boot loader. That will not hurt anything as long as that is the boot loader you are using.

Do you have any software in windows that uses DRM or some windows virus software thinks grub in the MBR is a rootkit? Have you hibernated in windows and written data into windows from Ubuntu. Those can cause huge problems.

I suggest if your windows recovery partition lets you make a repair CD, you do that or download one. You want a repair CD or liveCD for every operating system you have installed.

Also if it creates DVDs you make those and delete the recovery partition. The recovery DVD does not actually install windows but is an image that just restores your computer to the way it was the day you bought it. You may also want to make a full back up of your windows so you do not have to restore, update and reinstall everything all over again with the many reboots required that the recovery would require.

Good to have a full backup:
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by jmvizanko on 2011-04-19
> **oldfred said:**
> Do you have any software in windows that uses DRM or some windows virus software thinks grub in the MBR is a rootkit? Have you hibernated in windows and written data into windows from Ubuntu. Those can cause huge problems.

I turned hibernate off entirely on my computer, on the off chance it could be a problem.  I have viewed word documents from the mounted windows partition, and saved them with changes.  Would the correct way to do this be to create a shared partition?  Is it easy and safe enough to do this now that I already have both OS installed, and do you know of the best idiot proof guide to doing so?

---

### Post by oldfred on 2011-04-19
I am afraid nothing is totally idiot proof. I regularly screw up system, but part of the fun is then figuring out how to fix it.:)

You need to keep lots of room in your NTFS partition or Linux partitions. At least 20% free for windows. But you can shrink any partition that has lots of room,  and then  create a NTFS partition for data. It can be either primary or logical where ever is easier.

I keep photos, Firefox profiles, Thunderbird profiles & some data in my shared. When I used XP a lot I found various apps that stored data all over the place, sometime in My Docs, somes apps, sometimes inside the program files. So I wrote a .bat file just to copy to /shared and then I backed up /shared to have all my windows data. I still have the same data in my NTFS, but rarely use XP now. Just have not gotten to reorganizing, yet.

---

