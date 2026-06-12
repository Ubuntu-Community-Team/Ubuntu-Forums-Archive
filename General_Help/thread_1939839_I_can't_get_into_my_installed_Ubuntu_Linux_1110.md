---
title: "I can't get into my installed Ubuntu Linux 11/10"
date: 2012-03-12
forum: General Help
---

### Post by Jayhawker on 2012-03-12
For some reason I can't guess, since some day, suddenly, when it comes to the moment to choice between windows and ubuntu (I have ubuntu into windows by wubi), after some seconds it appears the following commands in black screen, and the result is I can't get into ubuntu linux 11/10:

Firts at all:

Try (hd,Ø): NTFS5: No wubildr
Try (hd,1): NTFS5: error: “prefix” is not set.

Some time after, it appears what follows: 

* Starting bluetooth								[ OK ]
* PulseAudio configured for per-user sessions
Saned disabled; 
edit(etc/default/saned [ OK ]

* Checking battery state…							[ OK ]

Sometimes it appears these other orders instead:

* Starting CUPs printing spooler/server					[ OK ]
* Starting System V runlevel compatibility				[ OK ]
* Starting CPU interrupts balancing daemon				[ OK ]
* Starting deferred execution scheduler					[ OK ]
* Starting regular background program processing daemon		[ OK ]
* Starting LightDM Display manager					[ OK ]
* Starting ACPI daemon							[ OK ]
* Starting bluetooth								[ OK ]

PulseAudio configured for per-user sessions
Saned disabled; 
edit(etc/default/saned [ OK ]


After a while, nothing more happens in the computer, so I decide to close the computer, and then it appears very briefly (hard to get it) what follows: 

Peech-dispatcher disabled; edit /etc/default/speech-dispatcher
Checking for running unattended-upgrades:
Acpid: exiting
SpamAssassin mail Filter Daemon: disabled, see /etc/default/spamassassin
•	Stopping bluetooth
•	Asking all remaining processes to terminate…
•	Killing all remaining processes…

modem manager [803]: «info» Caught signal 15, shutting down

•	Deconfiguring network interfaces…
•	Deactivating swap…

Umount: /run/lock: not mounted
	* Will now halt

Please, is any way to recover my installed 11/10 avoiding to reinstall it and consequently losing all my files and installed programs?

Thanks.

---

### Post by bcbc on 2012-03-12
You can access the \ubuntu\disks\root.disk through this tool [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) from windows readonly.

Or boot an Ubuntu CD and loop mount it. 

If you've had some hard shutdowns you might consider running chkdsk /f on windows and then 'fsck'ing the root.disk. Refer to the guide for more info: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Suparious on 2012-03-12
you could try the WUBI megathread [http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by Jayhawker on 2012-03-12
Thank You for your concern. Please how I apply this 'fsck' on the root disk? 

By the way, I think you are right, maybe it has been a hard shutdown.

Grateful again

> **bcbc said:**
> You can access the \ubuntu\disks\root.disk through this tool [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) from windows readonly.

Or boot an Ubuntu CD and loop mount it. 

If you've had some hard shutdowns you might consider running chkdsk /f on windows and then 'fsck'ing the root.disk. Refer to the guide for more info: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bcbc on 2012-03-12
The wubi guide has some info on that [here]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F")

Basically, you need to know what the partition the root.disk is on. You can find out easily using the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"), which also provides some useful diagnostic information. You'll need an Ubuntu CD or USB in order to fsck the root.disk and run the bootinfoscript.

This may or may not be the problem, but if you've had hard shutdowns you definitely should run the chkdsk as well if you haven't already.

---

### Post by Jayhawker on 2012-03-13
I'm grateful for all your concern, but, honestly, I don't know where to begin because I'm not an Ubuntu expert. I'm very confused. 

I can only inform that Ubuntu folder is not missing neither the root.disk, which is inside ubuntu folder. 

What's **Windows readonly**? 

Is the "bootinfoscript" a program to install when in Linux?

What's **'fsck'ing the root.disk**?

I can use the USB to enter in Ubuntu Linux in the provisional way (not installing it, which would be absurd because I have it installed yet and don't want to lose any file). 

Thanks for all your attention

---

### Post by Jayhawker on 2012-03-13
Please, 

Once inside Ubuntu 11/10 through the USB, how I check if there is any change in sections of the hard disk?

---

### Post by bcbc on 2012-03-13
"You can access the \ubuntu\disks\root.disk through this tool [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) from windows readonly." == From windows, you can download and run the ext2read program, point it at the file \ubuntu\disks\root.disk and it will give you read-only access to the files on it.

fsck == file system check. A utility that will check the integrity of the ext4 file system that the root.disk contains.

bootinfoscript is a bash script you can download and run that provides useful diagnostic information. It does require full access to your computer, but it is open source and used so commonly it's highly unlikely to be a risk.

You can also get your files off the root.disk by booting an Ubuntu CD/USB, selecting 'try ubuntu' and then mounting the host partition (ntfs or fat32) and then 'loop mounting' the root.disk. I can give you exact commands but I need to know what partition the root.disk is on first. If you know this, let me know, or else post the result of the bootinfoscript.

---

### Post by Jayhawker on 2012-03-14
Thanks a lot for your help. 

The results of bootinfoscript are: 

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda2/Wubi for information... 
Searching sda3 for information... 
Searching sdb1 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".

Nevertheless, no "results.txt" file has appeared at my desktop. Maybe because I'm in "try Ubuntu" mode. 

I'm looking forward to hearing from you, really!

Thanks again 

> **bcbc said:**
> "You can access the \ubuntu\disks\root.disk through this tool [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) from windows readonly." == From windows, you can download and run the ext2read program, point it at the file \ubuntu\disks\root.disk and it will give you read-only access to the files on it.

fsck == file system check. A utility that will check the integrity of the ext4 file system that the root.disk contains.

bootinfoscript is a bash script you can download and run that provides useful diagnostic information. It does require full access to your computer, but it is open source and used so commonly it's highly unlikely to be a risk.

You can also get your files off the root.disk by booting an Ubuntu CD/USB, selecting 'try ubuntu' and then mounting the host partition (ntfs or fat32) and then 'loop mounting' the root.disk. I can give you exact commands but I need to know what partition the root.disk is on first. If you know this, let me know, or else post the result of the bootinfoscript.

---

### Post by Jayhawker on 2012-03-14
Sorry, 

I finally found the "results.txt" file. I add it here but I know it is very long. I very appreciate your concern. Here it goes:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd /wubildr

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 20110518
    Boot sector info:   Syslinux looks at sector 319104 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   288,114,687   287,705,088   7 NTFS / exFAT / HPFS
/dev/sda3         288,114,688   312,578,047    24,463,360   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2024 MB, 2024275968 bytes
16 heads, 32 sectors/track, 7722 cylinders, total 3953664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,953,151     3,953,120   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       520330a2-60cd-4ccf-b939-94754e4c1657   ext3       
/dev/sda1        BC906591906552C6                       ntfs       SYSTEM
/dev/sda2        0EBA3993BA3977F3                       ntfs       
/dev/sda3        9066D8D466D8BC62                       ntfs       RECOVERY
/dev/sdb1        2C1D-4F2B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 0EBA3993BA3977F3
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 0EBA3993BA3977F3
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
  set locale_dir=($root)/boot/grub/locale
  set lang=ca_ES
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, amb Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 0EBA3993BA3977F3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=0EBA3993BA3977F3 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, amb Linux 3.0.0-16-generic (mode de restabliment)' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 0EBA3993BA3977F3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	echo	'Carregant Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=0EBA3993BA3977F3 loop=/ubuntu/disks/root.disk ro single 
	echo	'S'\''està carregant la ramdisk inicial ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, amb Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 0EBA3993BA3977F3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=0EBA3993BA3977F3 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, amb Linux 3.0.0-12-generic (mode de restabliment)' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 0EBA3993BA3977F3
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	echo	'Carregant Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=0EBA3993BA3977F3 loop=/ubuntu/disks/root.disk ro single 
	echo	'S'\''està carregant la ramdisk inicial ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
--------------------------------------------------------------------------------

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk	none	swap	sw	0	0
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic              55
               =                boot/initrd.img-3.0.0-16-generic              192
               =                boot/vmlinuz-3.0.0-12-generic                 20
               =                boot/vmlinuz-3.0.0-16-generic                 46
               =                initrd.img.old                                 7
               =                vmlinuz                                       46
               =                vmlinuz.old                                   20

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by bcbc on 2012-03-14
To fsck:
```
sudo mount /dev/sda2 /mnt
sudo fsck /mnt/ubuntu/disks/root.disk
```

NOTE:
I am assuming you've already run 'chkdsk /f' - do that before fscking. Also don't run fsck if you've mounted the root.disk.

---

### Post by Jayhawker on 2012-03-14
Yes, I have already run 'chkdsk /f'. I don't have mounted the root.disk.

Must I write in a row both orders? Or rather must I run the first, and then the second one?

In any case, must I give to you the results?

Thanks


QUOTE=bcbc;11765306]To fsck:
```
sudo mount /dev/sda2 /mnt
sudo fsck /mnt/ubuntu/disks/root.disk
```

NOTE:
I am assuming you've already run 'chkdsk /f' - do that before fscking. Also don't run fsck if you've mounted the root.disk.[/QUOTE]

---

### Post by bcbc on 2012-03-14
Enter each line separately. If the first doesn't succeed, the second will also fail.

You don't need to give the results, but it'd be nice to know whether it fixes the problem - maybe there are some other things to try if it doesn't work.

---

### Post by Jayhawker on 2012-03-15
As for the first order, after a first try without results,the second one offers what follows:

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt

Mount is denied because the NTFS volume is already exclusively opened.

The volume may be already mounted, or another software may use it which

could be identified for example by the help of the 'fuser' command.

ubuntu@ubuntu:~$


The second order offers what is below:

ubuntu@ubuntu:~$ sudo fsck /mnt/ubuntu/disks/root.disk
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
/mnt/ubuntu/disks/root.disk: clean, 245822/3551232 files 7495448/28409856 blocks (it will be checked in 3 months)--

I must add that nothing has changed. The problem remains


Thank You for your concern

> **bcbc said:**
> Enter each line separately. If the first doesn't succeed, the second will also fail.

You don't need to give the results, but it'd be nice to know whether it fixes the problem - maybe there are some other things to try if it doesn't work.

---

### Post by jgcamp99 on 2012-03-15
Actually all you have to do is use the live cdrom and reinstall it over the original installation using the same exact user id & password when prompted to do so & install. **_Don't_ **format the hdd.

---

### Post by bcbc on 2012-03-15
> **Jayhawker said:**
> As for the first order, after a first try without results,the second one offers what follows:

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt

Mount is denied because the NTFS volume is already exclusively opened.

The volume may be already mounted, or another software may use it which

could be identified for example by the help of the 'fuser' command.

ubuntu@ubuntu:~$


The second order offers what is below:

ubuntu@ubuntu:~$ sudo fsck /mnt/ubuntu/disks/root.disk
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
/mnt/ubuntu/disks/root.disk: clean, 245822/3551232 files 7495448/28409856 blocks (it will be checked in 3 months)--

I must add that nothing has changed. The problem remains


Thank You for your concern

If you already mounted the drive (clicking on it from the Nautilus folder menu will do that) then just unmount it first. I guess you did that based on the fsck output.

Sometimes you need to force fsck to run even if the filesystem appears clean:
```
sudo fsck -f /mnt/ubuntu/disks/root.disk
```

If that doesn't make a difference, let's try:
1. boot to grub menu
2. hit 'E' on first menu entry
3. delete 'quiet splash vt.handoff=7' and hit CTRL+X to boot. Write down the lines shown when it hangs and report back. 

Thanks

---

### Post by Jayhawker on 2012-03-15
Nautilus folder menu? Sorry, I'm lost. 

How to boot to grub menu?

Not an Ubuntu connaisseur. Sorry and thanks for the help


> **bcbc said:**
> If you already mounted the drive (clicking on it from the Nautilus folder menu will do that) then just unmount it first. I guess you did that based on the fsck output.

Sometimes you need to force fsck to run even if the filesystem appears clean:
```
sudo fsck -f /mnt/ubuntu/disks/root.disk
```

If that doesn't make a difference, let's try:
1. boot to grub menu
2. hit 'E' on first menu entry
3. delete 'quiet splash vt.handoff=7' and hit CTRL+X to boot. Write down the lines shown when it hangs and report back. 

Thanks

---

### Post by Jayhawker on 2012-03-15
But If I do that, I'll lose all my files and documents, won't I?

> **jgcamp99 said:**
> Actually all you have to do is use the live cdrom and reinstall it over the original installation using the same exact user id & password when prompted to do so & install. **_Don't_ **format the hdd.

---

### Post by bcbc on 2012-03-15
Nautilus is just the Ubuntu's version of windows explorer. So when you click on the folder icon (file browser), that's nautilus. On the top left it lists 'devices' and if you click on a partition listed there, it will mount it and show you the contents. That's what I meant.

Okay I saw that earlier you didn't 'see anything between selecting Ubuntu and then getting stuck'. You're supposed to see the grub menu inbetween that. In some cases the menu doesn't show - if e.g. it's trying to display at a graphics resolution that's not supported. You can fix this by changing the grub boot options, but it's a little difficult if you can't boot at all... you could manually edit grub.cfg from a live CD, but that's getting a little bit involved.
How about wait 4 seconds between selecting "Ubuntu" and then hit 'E'. Hopefully you'll see the grub menu entry in the 'editor' and you can edit and Ctrl+X to boot. If nothing appears after a couple of seconds, just hit ESC and then enter to continue booting.

---

### Post by Jayhawker on 2012-03-19
The problem, when booting to grub menu, is that there is not any 'quiet splash vt.handoff=7' to erase

:)
 


> **bcbc said:**
> Nautilus is just the Ubuntu's version of windows explorer. So when you click on the folder icon (file browser), that's nautilus. On the top left it lists 'devices' and if you click on a partition listed there, it will mount it and show you the contents. That's what I meant.

Okay I saw that earlier you didn't 'see anything between selecting Ubuntu and then getting stuck'. You're supposed to see the grub menu inbetween that. In some cases the menu doesn't show - if e.g. it's trying to display at a graphics resolution that's not supported. You can fix this by changing the grub boot options, but it's a little difficult if you can't boot at all... you could manually edit grub.cfg from a live CD, but that's getting a little bit involved.
How about wait 4 seconds between selecting "Ubuntu" and then hit 'E'. Hopefully you'll see the grub menu entry in the 'editor' and you can edit and Ctrl+X to boot. If nothing appears after a couple of seconds, just hit ESC and then enter to continue booting.

---

