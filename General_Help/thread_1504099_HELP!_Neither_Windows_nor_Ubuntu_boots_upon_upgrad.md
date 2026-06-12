---
title: "HELP! Neither Windows nor Ubuntu boots upon upgrade"
date: 2010-06-07
forum: General Help
---

### Post by shuffguy on 2010-06-07
Please help! I'm desperate. I have a Dell XPS running Windows 7 on one internal hard drive and Ubuntu on another internal. I've been running both for two months without any problems. However, I decided to upgrade today to lucid lynx, and after the restart to complete the install, I'm taken to the Intel Matrix Storage Manager and given this 

error: no such device: bf06c4d8-88db-4695-9b15-2cd6698e14a1
grub rescue>

Nothing I do works and it won't boot into Windows or Ubuntu. Please someone help, I don't know what to do!

---

### Post by Snippa on 2010-06-07
I cannot exactly help solve your issue, but I can tell you that I did encounter this recently after messing up an attempted upgrade from Grub to Grub2.
Basically, the configuration of your Grub appears to be messed up. I cannot say what exactly the problem is though unfortunately, since I didn't look too much into it.

All I can recall at the moment is that it appears this line in the Grub config is likely what is causing the problem:
[FONT=monospace]
[/FONT]kernel /vmlinuz26 **root=**

Normally, that line will read something like this (depending on where root actually is):
kernel /vmlinuz26 **root=/dev/sda3 ro**

However, there are some cases where it can read a bit differently, including that bit of text after "error: no such device" in your post. That text I believe is the UUID of the the hard drive that is supposed to contain root.

For whatever reason, grub appears to not be finding root there.
Don't freak out, I think the solution may be very simple. I BELIEVE there was a command line solution for this, at least to be able to boot into linux.
Unfortunately, I cannot provide the solution. I hope what I've posted here will help you to find your solution or help anyone else who reads this to come up with the solution for you.
Sorry I couldn't be of more help.

---

### Post by shuffguy on 2010-06-07
That does sort of help, is the solution is simple. I'm really afraid because I have all of my data on one computer and I'm not sure what to do here. Thank you. Can you point me anywhere that would know?

Or does anyone else know?

---

### Post by wilee-nilee on 2010-06-07
Post this boot script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
This script will tell whats going on. I wouldn't try any fixes until you get some feedback, from the script. In a case like this what worked for me is not a good way of trying to fix it, and may render the whole thing much more difficult to fix or brick the OS's altogether.

---

### Post by wilee-nilee on 2010-06-07
n

---

### Post by oldfred on 2010-06-07
This suggests the UUID may be wrong. Did you change any partitions?

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

The boot info script will let us see if there is anything else and be able to compare UUID's.

---

### Post by shuffguy on 2010-06-07
Thank you guys. Okay, I'll make a live cd as soon as I get my laptop back and run the script. I didn't change the partitions I don't think, I just upgraded to Lucid Lynx. Could I have done something wrong? I mean, doubtless I did SOMETHING wrong.

Also, I have a lot of music stored on one of the internal hard drives. Normally I would have a backup, but this was the backup when my external broke down, and I'm still waiting for that. Hence, this is my only copy. Is there a chance that the data and music will be lost? Also, brick the OS? So the entire computer will just be ruined?

---

### Post by Smart Viking on 2010-06-07
> **shuffguy said:**
> Thank you guys. Okay, I'll make a live cd as soon as I get my laptop back and run the script. I didn't change the partitions I don't think, I just upgraded to Lucid Lynx. Could I have done something wrong? I mean, doubtless I did SOMETHING wrong.

Also, I have a lot of music stored on one of the internal hard drives. Normally I would have a backup, but this was the backup when my external broke down, and I'm still waiting for that. Hence, this is my only copy. Is there a chance that the data and music will be lost? Also, brick the OS? So the entire computer will just be ruined?

Not really, you can take out the hard disk and put them in another machine and transfer the files, so as long as the hard disks work, you files are safe. :)

---

### Post by shuffguy on 2010-06-08
Okay guys, I ran the boot script, here are the results. Thank you guys so much for this, I don't know what I would have done. I need my computer to work, this is helping so much. 

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 6819184 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 3348448 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 3369224 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb3 and 
                       looks at sector 3374720 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 3377696 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63        96,389        96,327  de Dell Utility
/dev/sdb2              98,304    31,555,583    31,457,280   7 HPFS/NTFS
/dev/sdb3    *     31,555,584   625,139,711   593,584,128   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   488,394,751   488,392,704   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       bf06c4d8-88db-469f-9b15-2cd6698e14a1   ext4                                     
/dev/sda1        0088866C88866050                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        07D8-021C                              vfat       DellUtility                   
/dev/sdb2        A0BAB7FABAB7CB54                       ntfs       RECOVERY                      
/dev/sdb3        3AF8842DF883E58B                       ntfs       OS                            
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        EA4457F04457BE4F                       ntfs       New Volume                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sdb3/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 3af8842df883e58b
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 3af8842df883e58b
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 3af8842df883e58b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sdb3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 3af8842df883e58b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sdb3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 3af8842df883e58b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 3af8842df883e58b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0088866c88866050
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdb3/Wubi: Location of files loaded by Grub: =================


   1.7GB: boot/grub/core.img
   1.7GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.31-14-generic
   1.8GB: boot/initrd.img-2.6.32-22-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .8GB: boot/vmlinuz-2.6.32-22-generic
   1.8GB: initrd.img
   1.7GB: initrd.img.old
    .8GB: vmlinuz
    .5GB: vmlinuz.old 
```

---

### Post by wilee-nilee on 2010-06-08
It would be great if you can to put the script in code tags just edit the post by doing this.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
This makes it much easier to read.

Also anyone wanting to help please note that this a wubi install.;)

---

### Post by shuffguy on 2010-06-08
Okay, done! I appreciate any reply or feedback you can give me.

---

### Post by wilee-nilee on 2010-06-08
> **shuffguy said:**
> Okay, done! I appreciate any reply or feedback you can give me.

This is beyond me like most things in life, but there are others who can help.;)

---

### Post by bcbc on 2010-06-08
OK you made a mistake at the part when it asked you where to install grub2. Since you have a wubi install, you should have not selected any drive or partition. Unfortunately the 'help text' is misleading, so you selected every drive and every partition.

You need to run testdisk to recover the boot sector on your windows partition (/dev/sda1 is the Windows 7 one). Instructions are here: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Then you need to restore the windows bootloader back to the drive master boot record (MBR). You can do this using a windows install/repair disk, but you can just as easily install an equivalent bootloader using the live CD from a terminal prompt.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Note for installing testdisk and lilo you need the universe repository enabled. From the live CD desktop, check System, Administration, Software sources. Then the first tab has a few  checkboxes, one of them is 'Universe'. Make sure it is checked.

---

### Post by oldfred on 2010-06-08
The maintainers do not consider it a bug since drives are different than partition. It is just in windows c: & d: are partitions but windows always calls them drives.

It is a bit of a hassle but please sign up and add your name to one who has this bug, include particularly that yours was a wubi install.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

bug reports info on how to do:
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by shuffguy on 2010-06-08
Okay, I installed lilo but lilo is asking me to install liloconfig(8) and I'm not sure what that is or where to get that. Is it a file on the computer?

And it gave me these warnings?

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian

Please, what do they mean?

---

### Post by bcbc on 2010-06-08
> **shuffguy said:**
> Okay, I installed lilo but lilo is asking me to install liloconfig(8) and I'm not sure what that is or where to get that. Is it a file on the computer?

And it gave me these warnings?

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian

Please, what do they mean?

You can ignore them. You will be using lilo in a form that is equivalent to the windows bootloader - it boots from the  partition marked active (/dev/sda1). 

If you were using it to boot ubuntu then they would apply - in that case you need the kernel and initial ramdisk.

But I encourage you to read the lilo manual before installing if you are unsure. either "man lilo" or look online. Alternatively, use your windows install dvd to install the windows bootloader.

---

### Post by shuffguy on 2010-06-08
IT WORKED! Hallelujah it worked! Thank you guys so much, I can boot safely into windows now! Is there anything else I need to do on the linux end? Or does this mean I fixed the Linux update mistake I made and now have Lucid Lynx installed on my computer?

---

### Post by bcbc on 2010-06-08
> **shuffguy said:**
> IT WORKED! Hallelujah it worked! Thank you guys so much, I can boot safely into windows now! Is there anything else I need to do on the linux end? Or does this mean I fixed the Linux update mistake I made and now have Lucid Lynx installed on my computer?

Awesome :)

If there were no other issues in the upgrade process your wubi lucid lynx should work fine. However, I've seen reports of wubi not booting after subsequent updates (following a successful upgrade). Since you have so much disk 'real estate' you might consider a conventional dual-boot install at some point.

By the way, if your original wubi install was with version 9.10 - if you haven't already - you need to replace your wubildr file. See this link for info: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by shuffguy on 2010-06-08
I thought I did have a conventiol dual boot install? I installed one os on one drive and one OS on another?

---

### Post by bcbc on 2010-06-08
> **shuffguy said:**
> I thought I did have a conventiol dual boot install? I installed one os on one drive and one OS on another?

Not exactly. While it's true you have a dual boot, the ubuntu is installed on a 'virtual disk'. This is an ntfs file (d:\ubuntu\disks\root.disk) that contains an ext4 formatted file system upon which ubuntu is installed. 

Every time you boot ubuntu, the virtual disk file is mounted, and - for all intents and purposes - is a partition on a real disk. 

Except that it's not. For example if you do a hard shutdown there is a risk that the ntfs file becomes corrupted, in which case you won't be able to boot ubuntu. (As opposed to a single file being corrupted, the whole virtual disk is corrupted).

Since I'm on the subject, keep backups of the root.disk file. If at any point you can't boot ubuntu, you can loop mount this file from a live cd and pull off data - or recover your entire ubuntu install if necessary. 

Read the wubi guide for more info: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)


PS. don't back up the root.disk in the same directory. If you ever uninstall ubuntu (from the Add/Remove programs under windows) it will delete the root.disk along with all the other wubi files and directories.

---

### Post by wilee-nilee on 2010-06-08
> **shuffguy said:**
> I thought I did have a conventiol dual boot install? I installed one os on one drive and one OS on another?

If you install from a live windows environment it is a wubi install. I have seen people build partitions rather then letting the wubi install just ask the file size.

I'm not real familiar with wubi though, glad your up and running. These people who helped can direct on a true dual boot if you want one.

---

### Post by shuffguy on 2010-06-08
Good to know, I think I will try that as soon as I make sure everything is correct. Thank you guys so much, I would have been lost without you, and if I have anymore problems I'll post them! Thanks again!

---

