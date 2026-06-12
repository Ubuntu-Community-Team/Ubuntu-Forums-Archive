---
title: "Triple Booting Win7 Xp ubuntu problem"
date: 2010-09-15
forum: General Help
---

### Post by Femio on 2010-09-15
The steps I took in doing this was


[LIST]
[*]Install xp
[*]Install win7
[*]Install ubuntu 10.04
[*]Used easybcd 2.02 to edit the bootloader
[/LIST]
The problem I am having is that every time I try to boot into Ubuntu i get this Error/Message 
```
Try (hd0,0) NTFS5: No Ang1
try (hd0,1) Ext2:
```On Easybcd I selected linux, selected Grub2, and I even rewrote the mbr to the vista loader like some one suggested, and yet I Still get the same message. Is there any way someone can post a link to a fix or just tell me? I would greatly appreciate it, either post here or email me at [EMAIL="femio04@gmail.com"]femio04@gmail.com[/EMAIL]

---

### Post by oldfred on 2010-09-15
I do not think you will get a lot of help here. Most of us use grub or grub2 as our boot loaders. A few use easyBCD to update their windows.

I would also take out your actual email in above post. You may get spammed as this site can be scanned. Better to use PM as that will also send you an email.

[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

Why not easyBCD - Herman's post
[http://ubuntuforums.org/showthread.php?t=1554155](http://ubuntuforums.org/showthread.php?t=1554155)

Grub2 is considered less reliable when installed to a partition as it has to use blocklist. Changes to files may required reinstall of grub where standard install is more tolerant of changes.

---

### Post by Mark Phelps on 2010-09-16
> **Femio said:**
> ... on Easybcd ...

These are the Ubuntu forums.  Folks here specialize in supporting GRUB for boot loading (and some, LILO as well).

For EasyBCD tech support, you should really go to the NeoSmart Technology EasyBCD forums.  They're the experts on configuring and using EasyBCD.

---

### Post by Femio on 2010-09-16
Well Thanks for the quick reply's, also I have seen many post about easybcd so I didn't know i wasn't alowed to ask for support... also Itried reinstalling grub2 as main bootloader but it still fails, I get to select between my other partions but when i go to pick ubuntu I get a error message saying "Target Filesystem doesn't have /sbin/init" and a line below that which i cannot remember. Even when I select windows booat loader it tried to load from sdb4 when my windows mbr is loaded on sdb1. I thought grub2 was suppose to actually detect the right partion but it hasn't

---

### Post by Roasted on 2010-09-16
> **Femio said:**
> Well Thanks for the quick reply's, also I have seen many post about easybcd so I didn't know i wasn't alowed to ask for support... 

It's not that you aren't allowed to ask for support here. We're just trying to be helpful and guide you to a place where you can get an answer much quicker for your benefit. After all, the reality is a user who's familiar with EasyBCD is very unlikely to hang around these forums, but more likely to hang around the forums suggested above.

Hopefully you find the answer you were looking for. If you end up needing help with grub, then you'd be in a place right here with tons of helpful users who could help you out. ;)

---

### Post by oldfred on 2010-09-16
If you have grub installed or just want to know what is where this will tell you. 

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Femio on 2010-09-16
Thanks will be posting up the bootscript shortly. Also I dont think easybcd is messing up the bootloader, because even in grub2 it still has errors


**edit: Here is the log**
*_I also notice that sda1 portion does not have win7/vista on it, its just a extra HDD I use as a storage device. I Don't know why its reading it like that or if it makes a difference but I just thought i mention it_*


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntdetect.com 
                       /grub/core.img /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
30 heads, 61 sectors/track, 266883 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   262,307,839   262,305,792   7 HPFS/NTFS
/dev/sdb2         262,309,320   434,333,339   172,024,020  83 Linux
/dev/sdb3         434,333,340   467,105,939    32,772,600  82 Linux swap / Solaris
/dev/sdb4         467,106,003   586,051,199   118,945,197   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F6BEC7B9BEC77123                       ntfs       Nig Files                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E4E4C38DE4C36082                       ntfs       Win7                          
/dev/sdb2        f2030f4b-12fe-4f9d-bcd0-c17cf08c53d6   ext3                                     
/dev/sdb3        9a680dc1-00fe-42e2-9bbf-8da3d6d4ad90   swap                                     
/dev/sdb4        DC009C3D009C2116                       ntfs       Xp                            
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sdb1/grub/grub.cfg: =============================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set f2030f4b-12fe-4f9d-bcd0-c17cf08c53d6
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set e4e4c38de4c36082
set locale_dir=($root)/grub/locale
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

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb4)" {
    insmod ntfs
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set dc009c3d009c2116
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: grub/core.img
    ??GB: grub/grub.cfg

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set f2030f4b-12fe-4f9d-bcd0-c17cf08c53d6
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set f2030f4b-12fe-4f9d-bcd0-c17cf08c53d6
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set f2030f4b-12fe-4f9d-bcd0-c17cf08c53d6
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f2030f4b-12fe-4f9d-bcd0-c17cf08c53d6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set f2030f4b-12fe-4f9d-bcd0-c17cf08c53d6
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f2030f4b-12fe-4f9d-bcd0-c17cf08c53d6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set f2030f4b-12fe-4f9d-bcd0-c17cf08c53d6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set f2030f4b-12fe-4f9d-bcd0-c17cf08c53d6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb4)" {
    insmod ntfs
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set dc009c3d009c2116
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=f2030f4b-12fe-4f9d-bcd0-c17cf08c53d6 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=9a680dc1-00fe-42e2-9bbf-8da3d6d4ad90 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 170.5GB: boot/grub/core.img
 170.5GB: boot/grub/grub.cfg
 170.6GB: boot/initrd.img-2.6.32-24-generic
 170.5GB: boot/vmlinuz-2.6.32-24-generic
 170.6GB: initrd.img
 170.5GB: vmlinuz

================================ sdb4/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER /NUMPROC=4
```

---

### Post by Femio on 2010-09-16
bump

---

### Post by Femio on 2010-09-17
any one? I would really appreciate some help

---

### Post by NuBiXx on 2010-09-17
> **Mark Phelps said:**
> These are the Ubuntu forums.  Folks here specialize in supporting GRUB for boot loading (and some, LILO as well).

For EasyBCD tech support, you should really go to the NeoSmart Technology EasyBCD forums.  They're the experts on configuring and using EasyBCD.

Someone should tell the author of the WindowsDualBoot Documentation because they mention using Easybcd.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Femio on 2010-09-19
> **NuBiXx said:**
> Someone should tell the author of the WindowsDualBoot Documentation because they mention using Easybcd.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I know about that, but that dosen't help my problems. Does any one know why Grub2 is failing aswell as Easybcd

---

### Post by wilee-nilee on 2010-09-19
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntdetect.com 
                       /grub/core.img /boot/grub/core.img


I'm not familiar with easybcd so maybe grub is supposed to be here. Generally grub in the ntfs partition is a problem, but with booting the windows OS.

Also sda1 looks to be first to be read in bios and has a bootflag on it, if this is the case I'm not sure if this is, but may be part of the problem. sda1 also has the lilo bootloader in its mbr.

I kind of surprised the easybcd people on the forum have not tried to help there are a few and some seem to know the setup fairly well.

---

### Post by Computer Guru on 2010-09-19
This is one of the known issues is in the Grub4Dos module used by EasyBCD, and generally points to something "wrong" with the filesystem structure on the disk (in this context, "wrong" means "unsupported"). That's why I'm not surprised to hear that also GRUB2 has issues with your setup - the basic underpinnings are the same.

On the root of one of your Windows partitions, you'll find a "ANG1" file created by EasyBCD. This contains the actual code that boots Ubuntu.

What you can try is to copy this file to any and all partitions on your system. Grub4Dos is searching for this file, and in the middle of its search it's coming across an ext2/3/4 partition that causes it to hang.

Most likely, placing ANG1 on (hd0,0) (which is the last partition before the hang) will work.

---

### Post by Femio on 2010-09-20
> **Computer Guru said:**
> This is one of the known issues is in the Grub4Dos module used by EasyBCD, and generally points to something "wrong" with the filesystem structure on the disk (in this context, "wrong" means "unsupported"). That's why I'm not surprised to hear that also GRUB2 has issues with your setup - the basic underpinnings are the same.

On the root of one of your Windows partitions, you'll find a "ANG1" file created by EasyBCD. This contains the actual code that boots Ubuntu.

What you can try is to copy this file to any and all partitions on your system. Grub4Dos is searching for this file, and in the middle of its search it's coming across an ext2/3/4 partition that causes it to hang.

Most likely, placing ANG1 on (hd0,0) (which is the last partition before the hang) will work.

Okay first of all I want to thank you for your response.

 I was able to get a little bit further but, once I got into the grub2 selection part, and selected Ubuntu I got this error

```
Target filesystem doesn't have /sbin/init
run-init: /etc/init: Permission denied
[    2.298635} Kernal panic - not syncing: Attempted to kill init
```This is the same error I get if I just use Grub2 instead of Easybcd. Any fix or suggestions for this?

---

### Post by Computer Guru on 2010-09-20
Either Ubuntu wasn't installed right (i.e. you _really_ don't have a /sbin/init) or the GRUB2 configuration file is loading the wrong partition, or GRUB2 is loading the right partition but due to a bug it cannot see the files on that partition.

---

### Post by Femio on 2010-09-20
I think its loading the wrong partion because I have ran ubuntu before, but I did somthing and I can't remember what it was that messed up the bootloader(I think it was upgrading bcd). So when I saw that I tried reinstalling Grub2 and I got that error I posted. 

*p.s I also noticed that when I try selection windows loader from Grub2  it tries to load from sda3 or 4(can't remeber which one but its def. one of them) but, I have all my OS installed on sdb.. I also tried reinstalling Grub2 to make sure that grub was installed correctly and on sdb and for some reason it keeps trying to load both my windows OS from Sda.*

---

### Post by wilee-nilee on 2010-09-20
Not sure if this is pertinent but sda is the external and it has a lilo bootloader which would boot windows. Which HD is first to be read in bios? sda also has a boot flag on it which can be removed if needed.

sdb2 is your Linux partition if you reloaded grub2 did you mount that partition, before reboot? How did you reload grub2?

---

### Post by Femio on 2010-09-20
My OS HDD loads first, so I have no idea why my extra hard drive is set to sda. I was also thinking I might have to remove the mbr from my extra hard drive(the sda) but, I have no idea on how to do this.
[B]
edit: I reread your post and realize what you were saying about sda so disregard my comment about that. To answer your last question, I used the method on the grub help page to reinstalling grub from the live cd and I did mount the sdb.[/B]

---

### Post by wilee-nilee on 2010-09-20
> **Femio said:**
> My OS HDD loads first, so I have no idea why my extra hard drive is set to sda. I was also thinking I might have to remove the mbr from my extra hard drive(the sda) but, I have no idea on how to do this.
[B]
edit: I reread your post and realize what you were saying about sda so disregard my comment about that. To answer your last question, I used the method on the grub help page to reinstalling grub from the live cd and I did mount the sdb.[/B]

Have you tried booting without the external plugged in?

The bootloader in sda is lilo and it has a bootflag on it, I'm just wondering if your loading with the lilo instead of grub in sdb.

I have never seen a bootscript with somebody running EasyBCD so I'm not sure what is supposed to be in the mbr.

---

### Post by Computer Guru on 2010-09-20
> **wilee-nilee said:**
> I have never seen a bootscript with somebody running EasyBCD so I'm not sure what is supposed to be in the mbr.

EasyBCD doesn't touch the MBR or the bootsector, so the MBR would be the standard Windows MBR. It just loads the bootsector of the active partition on the boot disk.
You can view all its gory details here: [http://mirror.href.com/thestarman/asm/mbr/Win2kmbr.htm](http://mirror.href.com/thestarman/asm/mbr/Win2kmbr.htm)

---

### Post by wilee-nilee on 2010-09-20
> **Computer Guru said:**
> EasyBCD doesn't touch the MBR or the bootsector, so the MBR would be the standard Windows MBR. It just loads the bootsector of the active partition on the boot disk.
You can view all its gory details here: [http://mirror.href.com/thestarman/asm/mbr/Win2kmbr.htm](http://mirror.href.com/thestarman/asm/mbr/Win2kmbr.htm)


Thats what I thought he has grub in the mbr, and a external with lilo first in boot so I wonder if lilo is getting them into windows.

OP we might wait for a answer here but it may be just getting the W7 bootloader in sdb is what is needed. I can give you a link to a recovery cd and the command if needed but lets wait for a solid answer.

---

### Post by Computer Guru on 2010-09-20
Why would having different bootloaders on the different disks' MBRs cause GRUB2 to load the wrong partition?

---

### Post by wilee-nilee on 2010-09-20
> **Computer Guru said:**
> Why would having different bootloaders on the different disks' MBRs cause GRUB2 to load the wrong partition?

My thought as well, you would know whats up more then myself.

If you look at the script though, it has lilo in one the sda external first in the bios, with a boot flag, with no OS. I don't think the boot flag matters but I just noticed it. The sdb is the one with Ubuntu and W7 and has grub in the mbr and grub files in the ntfs partition. Now I have no clue as to what this line should look like.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   [B]/grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntdetect.com 
                       /grub/core.img /boot/grub/core.img
[/B]

Normally grub in this area is a big deal and windows wont boot, so I am a bit stymied here. 


So on the forums we see people using grub, and dual booting with Windows. Generally it seems if grub is installed in another mbr then the one holding the OS,  this causes problems at times, not sure why.

But as it is if the OP is actually getting into windows now, it might be through the lilo loader, which may be just fine I don't know. There is no standard W7 bootloader in either mbr, but lilo will load windows, but it is just not on the same HD as either of the two OS.

I appreciate your help here, I need to get a EasyBCD user to post a bootscipt so I can get to know this program better.
 
I will let it go after this I am pretty familiar with boot problems but just not the EasyBCD setup. I recognize it as you have described it's role.

---

### Post by Computer Guru on 2010-09-20
That is weird!

/grub/core.img /boot/grub/core.img

These files shouldn't be on the Windows partition - at any rate, EasyBCD did not put them there.

Windows doesn't need much to boot - it actually doesn't need neither a Windows MBR nor a Windows bootsector. Much like GRUB, all that needs to happen is that BOOTMGR is loaded (vs Core.img)

So if his lilo script is coded to load /bootmgr from the Windows partition, then that's all it takes.

I'm not sure if you're asking a different question, though?

EasyBCD configured out-of-the-box for an Ubuntu GRUB2 entry would have

/BOOTMGR - the Windows bootloader
/BOOT/BCD - the Windows bootloader's menu file
/ANG# - the EasyBCD chainloader file (# is any digit to make it unique)
/NST/ANG#.mbr - the file that EasyBCD adds to the Windows boot menu, whose job is to search and load /ANG# from all partitions.

/ANG# is coded to search all partitions for /boot/grub/core.img or /grub/core.img and load it.

So you would have
BIOS -> HD0 -> Active Partition -> BOOTMGR -> /NST/ANG#.mbr -> /ANG# -> /boot/grub/core.img -> Ubuntu Kernel

But if he has extra copies of /boot/grub/core.img littered around his harddisk, ANG will possibly load the wrong copy.
It's important to note that to make EasyBCD one-click setup, no disk information is hard-coded anywhere. EasyBCD will search for /ANG# on all partitions, and the first one it finds it will load (with a specific #, of course). And /ANG# will search all partitions for /boot/grub/core.img and the first one it finds, it will load.

---

### Post by wilee-nilee on 2010-09-20
> **Computer Guru said:**
> That is weird!

/grub/core.img /boot/grub/core.img

These files shouldn't be on the Windows partition - at any rate, EasyBCD did not put them there.

Windows doesn't need much to boot - it actually doesn't need neither a Windows MBR nor a Windows bootsector. Much like GRUB, all that needs to happen is that BOOTMGR is loaded (vs Core.img)

So if his lilo script is coded to load /bootmgr from the Windows partition, then that's all it takes.

I'm not sure if you're asking a different question, though?

EasyBCD configured out-of-the-box for an Ubuntu GRUB2 entry would have

/BOOTMGR - the Windows bootloader
/BOOT/BCD - the Windows bootloader's menu file
/ANG# - the EasyBCD chainloader file (# is any digit to make it unique)
/NST/ANG#.mbr - the file that EasyBCD adds to the Windows boot menu, whose job is to search and load /ANG# from all partitions.

/ANG# is coded to search all partitions for /boot/grub/core.img or /grub/core.img and load it.

So you would have
BIOS -> HD0 -> Active Partition -> BOOTMGR -> /NST/ANG#.mbr -> /ANG# -> /boot/grub/core.img -> Ubuntu Kernel

But if he has extra copies of /boot/grub/core.img littered around his harddisk, ANG will possibly load the wrong copy.
It's important to note that to make EasyBCD one-click setup, no disk information is hard-coded anywhere. EasyBCD will search for /ANG# on all partitions, and the first one it finds it will load (with a specific #, of course). And /ANG# will search all partitions for /boot/grub/core.img and the first one it finds, it will load.

I never thought EasyBCD put the grub files in the ntfs partition, this happens when people don't know where they are putting them generally, this probably happened in a grub upgrade where your asked where you want it, or during the reloading.

Personally if my set up got like this which it never would, I would just reinstall the whole setup W7 and Ubuntu and setup the boot as it pleases me. For the OP this seems to be EasyBCD2, which I have no problems with really in the end it is all about just having a stable setup.

Thanks for your help here and the links.

OP, it really is up to what you want to do after you look through all this.

---

### Post by Femio on 2010-09-20
> **wilee-nilee said:**
> Have you tried booting without the external plugged in?

The bootloader in sda is lilo and it has a bootflag on it, I'm just wondering if your loading with the lilo instead of grub in sdb.

I have never seen a bootscript with somebody running EasyBCD so I'm not sure what is supposed to be in the mbr.

yea I tried that but still get the same results, I Don't know what is going wrong, but once I back up all my Info I guess I will try reinstalling all three of my OS again

---

### Post by wilee-nilee on 2010-09-20
> **Femio said:**
> yea I tried that but still get the same results, I Don't know what is going wrong, but once I back up all my Info I guess I will try reinstalling all three of my OS again

Feel free to ask us for help, somehow grub was put into the sdb1 ntfs, and it is kind of hard to say where any or all the problem are or what they are. If you decide to use EasyBCD2 again though, as was suggested, you might want to at the least have a thread or check in with their forum as well.

There are people on this forum who are familiar with using this program, but it is generally not the people who are really the specialist in this boot area. We use lilo or grub2 they work just fine and are quite stable if you know how to use them correctly.

---

### Post by Femio on 2010-09-20
Ok I finnaly got Ubuntu to load in Grub2 by just reinstalling ubuntu all over again but, the problem I run into now is that grub2 tries to load windows mbr from sdb4 when it should be loading it from sdb1. How would I go about fixing this problem?

---

### Post by wilee-nilee on 2010-09-20
> **Femio said:**
> Ok I finnaly got Ubuntu to load in Grub2 by just reinstalling ubuntu all over again but, the problem I run into now is that grub2 tries to load windows mbr from sdb4 when it should be loading it from sdb1. How would I go about fixing this problem?

If your still using EasyBCD2, I can't help, but I do wish you good luck in a supportive way.;)

---

### Post by Femio on 2010-09-20
I am using grub2

---

### Post by wilee-nilee on 2010-09-20
> **Femio said:**
> I am using grub2

Post the boot script again, You had grub in sdb1 and this has to be removed, can't give you any guarantees here though, as I would have reinstalled all the other OS. 

Without me having to read every word again in this thread are you completely backed up, with what is in the two windows set ups and do you have the ability to reinstall them. I'm just kind of busy, and I want to be safe here. ;)

College starts next week and I am multitasking here and I'm not so good at that.

Grub just needs to have a update with everything correct in Windows boot set up to boot the correct partition and to have the correct Windows booting partition active=bootflag in gparted. You installed XP before W7, XP is the boot partition to get to the windows boot menu. On the previous script you had the sdb1 partition as active=bootflag when it should be sdb4 the XP partition.

---

### Post by wilee-nilee on 2010-09-20
Sorry for the double post.

Just for fun from the live Ubuntu cd go to gparted and make sure that the ntfs partitions are unmounted and move the boot flag to sdb4 if it is still XP . In other words put it on XP. Then reboot and choose XP to boot. I forget what it looks like on grub with two MS on there so I think you get the drift. You just right click on the XP partition and manage flags and tick flag then hit the check icon to run the change.

---

### Post by drs305 on 2010-09-20
As I've told wilee-nilee, I know very little about Windows booting and even less about BCD.

But I wondered since you have Grub2 working, from the Grub command prompt what happens if you:

```
set root=(hd1,1)
chainloader +1
boot

```
Or:

```
chainloader (hd1,1)+1
boot
```

But as was mentioned, it's probably time to post another bootinfo script results.

---

### Post by Femio on 2010-09-21
> **wilee-nilee said:**
> Sorry for the double post.

Just for fun from the live Ubuntu cd go to gparted and make sure that the ntfs partitions are unmounted and move the boot flag to sdb4 if it is still XP . In other words put it on XP. Then reboot and choose XP to boot. I forget what it looks like on grub with two MS on there so I think you get the drift. You just right click on the XP partition and manage flags and tick flag then hit the check icon to run the change.

Here is my Log
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntdetect.com /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
30 heads, 61 sectors/track, 266883 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   262,307,839   262,305,792   7 HPFS/NTFS
/dev/sdb2         262,309,320   434,333,339   172,024,020  83 Linux
/dev/sdb3         434,333,340   467,105,939    32,772,600  82 Linux swap / Solaris
/dev/sdb4         467,106,003   586,051,199   118,945,197   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F6BEC7B9BEC77123                       ntfs       Nig Files                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E4E4C38DE4C36082                       ntfs       Win7                          
/dev/sdb2        225c22ca-e656-4a77-b98a-a183a15fc772   ext3                                     
/dev/sdb3        9a680dc1-00fe-42e2-9bbf-8da3d6d4ad90   swap                                     
/dev/sdb4        DC009C3D009C2116                       ntfs       Xp                            
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext3       (rw,errors=remount-ro)


=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 225c22ca-e656-4a77-b98a-a183a15fc772
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 225c22ca-e656-4a77-b98a-a183a15fc772
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 225c22ca-e656-4a77-b98a-a183a15fc772
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=225c22ca-e656-4a77-b98a-a183a15fc772 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 225c22ca-e656-4a77-b98a-a183a15fc772
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=225c22ca-e656-4a77-b98a-a183a15fc772 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 225c22ca-e656-4a77-b98a-a183a15fc772
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 225c22ca-e656-4a77-b98a-a183a15fc772
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb4)" {
    insmod ntfs
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set dc009c3d009c2116
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=225c22ca-e656-4a77-b98a-a183a15fc772 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=9a680dc1-00fe-42e2-9bbf-8da3d6d4ad90 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 201.2GB: boot/grub/core.img
 201.2GB: boot/grub/grub.cfg
 201.2GB: boot/initrd.img-2.6.32-24-generic
 201.1GB: boot/vmlinuz-2.6.32-24-generic
 201.2GB: initrd.img
 201.1GB: vmlinuz

================================ sdb4/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER /NUMPROC=4
```

I switched back to Easybcd and it runs smooth but, when it loads grub2 it still has xp set to the main bootloader. Even though on the logs it clearly shows windows 7 partion as the main

---

### Post by wilee-nilee on 2010-09-21
next

---

### Post by wilee-nilee on 2010-09-21
I think actually it may just be the boot flag now it is on sdb1. When you install XP then any other MS like Vista or W7 the second install puts its boot information in XP. XP is your boot partition if everything is normal. Change it as I described earlier; in gparted, from a live Ubuntu cd, or make sdb4 active in what every way windows disc manager does it. 

You may need to run **sudo update-grub** in Ubuntu after making this flag change.

With multiple MS installs the first install is the partition that should have the boot flag showing in gparted and the script. It is the boot partition, I hope this makes sense to you.

Instead of this 
/dev/sdb1   ** * **         2,048   262,307,839   262,305,792   7 HPFS/NTFS
/dev/sdb2         262,309,320   434,333,339   172,024,020  83 Linux
/dev/sdb3         434,333,340   467,105,939    32,772,600  82 Linux swap / Solaris
/dev/sdb4         467,106,003   586,051,199   118,945,197   7 HPFS/NTFS


You want this.
/dev/sdb1               2,048   262,307,839   262,305,792   7 HPFS/NTFS
/dev/sdb2         262,309,320   434,333,339   172,024,020  83 Linux
/dev/sdb3         434,333,340   467,105,939    32,772,600  82 Linux swap / Solaris
/dev/sdb4    ** * **   467,106,003   586,051,199   118,945,197   7 HPFS/NTFS

The external still looks to be being read first at boot though, not sure why, if you have looked in the bios to make sure it isn't.

---

### Post by richf on 2010-11-04
Try (hd0,0) NTFS5: No Ang1
try (hd0,1) Ext2:

I just got the same message when booting into Ubuntu 10.10. I dual-boot w/ Win 7 using EasyBCD. I have no idea how it happened; but to fix it, I used EasyBCD. 

I deleted the Ubuntu entry and re-added it.

All works fine now.

Hope this helps.

---

