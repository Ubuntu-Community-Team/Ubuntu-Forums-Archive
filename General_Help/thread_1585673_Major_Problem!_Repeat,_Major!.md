---
title: "Major Problem! Repeat, Major!"
date: 2010-09-30
forum: General Help
---

### Post by Gameboyman99 on 2010-09-30
Umm... Hi. Embarrassed now, I've had wayyyyy too many probs w/ my PC(It's too old).

  I had just updated Ubuntu, and a restart was required. so I did. _**After I restarted, Ubuntu will not start up, neither will GRUB!**_ This error message(I think this's what it says) came up for a billionth of a second:
1st screen says [B]Try hd(0,0) NTFS5
[/B]Which I think is different than what it was b4, but I dunno
2nd screen
```
Error: unknown command - loadfront
Error: File not found
```P.S. I'm using BOOT.INI to load:
```
[boot loader]
timeout=5
default=C:\wubildr.mbr
[operating systems]
C:\wubildr.mbr = "Ubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```P.P.S. It is modified;
P.P.P.S. Ya, I'm freaking out; but just a little;
help;
help;
help;

---

### Post by andrewthomas on 2010-10-01
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by mrhhug on 2010-10-01
run a fitness test on hard drive, memtests on your RAM - these things fail all the time especially in older computers

---

### Post by bcbc on 2010-10-01
I've been seeing a couple of these cropping up now. And there were a few a few months back that people managed to resolve by booting a live CD and editing the wubi grub. It's worth a try, let us know if it works. 

[http://ubuntuforums.org/showthread.php?t=1584714](http://ubuntuforums.org/showthread.php?t=1584714)

---

### Post by Gameboyman99 on 2010-10-01
It's not a HDD or memory failure; Windows still works and this happened right after I updated Ubuntu(Once I fix it I should look at my updated items...)

Thx for the links, and they almost work, except: how do I edit grub.cfg if I'm running off the live cd?? It's all replaced by the current(the cd's) default folders :(

EDIT: nothing at all is wrong w/ WUBI; I don't think...

---

### Post by andrewthomas on 2010-10-01
If you are still having problems go to :

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions and reply with the results in your next post

---

### Post by bcbc on 2010-10-01
> **Gameboyman99 said:**
> 
Thx for the links, and they almost work, except: how do I edit grub.cfg if I'm running off the live cd?? It's all replaced by the current(the cd's) default folders :(


You have to mount the wubi root.disk first to edit the grub.cfg. This was the thread I was referring to [http://ubuntuforums.org/showpost.php?p=9640093&postcount=30](http://ubuntuforums.org/showpost.php?p=9640093&postcount=30) in which the users root.disk was on /dev/sda2 ( you will need to change /dev/sda2 to whatever partition your root.disk is on). 

But do the bootinfoscript first anyway - that always provides a clearer picture of what is going on

---

### Post by Gameboyman99 on 2010-10-01
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.0 GB, 40981118976 bytes
240 heads, 63 sectors/track, 5293 cylinders, total 80041248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,015,039    80,014,977   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    78,156,224    78,156,162   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       d63ad01c-5399-42c3-bc23-69d4776c8f7d   ext4                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        6E1CE4461CE40B43                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        48C30D2134D43A57                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /win                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=5 
default=C:\wubildr.mbr 
[operating systems] 
C:\wubildr.mbr = "Ubuntu" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 6e1ce4461ce40b43
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 6e1ce4461ce40b43
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
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e1ce4461ce40b43
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e1ce4461ce40b43
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e1ce4461ce40b43
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e1ce4461ce40b43
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e1ce4461ce40b43
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e1ce4461ce40b43
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e1ce4461ce40b43
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   6.9GB: boot/grub/grub.cfg
   2.7GB: boot/initrd.img-2.6.32-21-generic
   1.4GB: boot/initrd.img-2.6.32-24-generic
   3.6GB: boot/initrd.img-2.6.32-25-generic
   3.2GB: boot/vmlinuz-2.6.32-21-generic
   3.5GB: boot/vmlinuz-2.6.32-24-generic
   3.5GB: boot/vmlinuz-2.6.32-25-generic
   3.6GB: initrd.img
   1.4GB: initrd.img.old
   3.5GB: vmlinuz
   3.5GB: vmlinuz.old
```

Annnd: how do I get to **sda1/Wubi/boot/grub/grub.cfg**???

---

### Post by bcbc on 2010-10-01
Mount wubi
```

sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

```
Edit wubi grub.cfg
```

sudo nano /mnt/boot/grub/grub.cfg

```
Comment out lines as follows
```

#if loadfont /usr/share/grub/unicode.pf2 ; then
# set gfxmode=640x480
# insmod gfxterm
# insmod vbe
# if terminal_output gfxterm ; then true ; else
# # For backward compatibility with versions of terminal.mod that don't
# # understand terminal_output
# terminal gfxterm
# fi
#fi

```
Save changes CTRL+X and reboot.

Give that a go.

---

### Post by Gameboyman99 on 2010-10-01
**/mnt** !?!?!!! That's where all my things are when I boot from the live cd??!! Hmmm, extremely useful... I am trying your suggestion now...
EDIT: The only reason I haven't tried this b4 is because I didn't know **grub.cfg** was in **/mnt**

---

### Post by Gameboyman99 on 2010-10-01
Yesssss!!:P Thx 4 specifying **/mnt**! Now I have 6 menu choices in GRUB but I now how to get rid of the xtras.
Thx again all u guys!!

UPDATE: It wuz an upgrade to a new Linux kernel; it prolly just dint install correctly or something

---

### Post by bcbc on 2010-10-01
> **Gameboyman99 said:**
> Yesssss!!:P Thx 4 specifying **/mnt**! Now I have 6 menu choices in GRUB but I now how to get rid of the xtras.
Thx again all u guys!!

Great!

To tweak grub2 [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

PS every time you run "update-grub" it's going to wipe out those changes you just made. So this isn't a long term fix to your problem. I'm not sure what to suggest for a permanent fix. You can try: ```
sudo grub-install /dev/sda1
```

This will update the wubildr on /host (i.e. c:\wubildr). But before you run it back up the original c:\wubildr in case it breaks. Also, if you get any message about needing --force don't do it. Wubi installs have a special override for this command - that currently only works when wubi is on the same partition as windows.

In the long run you probably want to migrate your wubi install to a partition. This is more stable mainly due to the issues with grub and wubi lately. Here's a howto migrate: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Mountjudo on 2010-10-29
Hi, I am a complete newbie so I apologize if I am wanting something obvious to be explained.
I have the same problem as the one here and I have the same output on screen
I dual-boot ubuntu and 7 using wubi and after restarting after upgrading from 10.04 to 10.10 I got the same result (unknown command "loadfont") and the screen hangs there.
I don't understand how to do the solution because I can only access windows 7 right now (ubuntu just hangs there) so where can I find the files I need to modify and how should I modify them as to not screw anything up.

Thanks.

---

### Post by bcbc on 2010-10-29
> **Mountjudo said:**
> Hi, I am a complete newbie so I apologize if I am wanting something obvious to be explained.
I have the same problem as the one here and I have the same output on screen
I dual-boot ubuntu and 7 using wubi and after restarting after upgrading from 10.04 to 10.10 I got the same result (unknown command "loadfont") and the screen hangs there.
I don't understand how to do the solution because I can only access windows 7 right now (ubuntu just hangs there) so where can I find the files I need to modify and how should I modify them as to not screw anything up.

Thanks.
This post has a fix that can be done from windows.
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

I don't believe the fix is permanent. But follow the bug linked within that post and then when a final fix comes out you'll know about it.

---

