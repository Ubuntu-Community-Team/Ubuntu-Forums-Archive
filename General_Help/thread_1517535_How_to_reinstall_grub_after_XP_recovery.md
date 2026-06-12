---
title: "How to reinstall grub after XP recovery ?"
date: 2010-06-25
forum: General Help
---

### Post by user1001 on 2010-06-25
Hi,

so How do you reinstall grub after XP recovery ?
btw I only have the live cd on a usb.. not the live cd it self.

thanks.

---

### Post by burton247 on 2010-06-25
Can you boot using the USB?

---

### Post by user1001 on 2010-06-25
Yep :) it's exactly like the live cd, but it's on the USB

---

### Post by wilee-nilee on 2010-06-25
What distro is it and which grub is it using, legacy or grub2?

---

### Post by user1001 on 2010-06-25
> **wilee-nilee said:**
> What distro is it and whch grub is it using? legacy or grub2

I think it's grub 2, but Im not sure, and also it's 10.04 LTS from the week it came out.

---

### Post by wilee-nilee on 2010-06-25
Just follow this link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by burton247 on 2010-06-25
okie dokie then

When you're in your liveCD load up a terminal and type 

```

grub

```

maybe sudo grub not too sure but this will put in in grub command thingy.

then locate where grub is installed

```

find /boot/grub/stage1

```

then it should give you hd(x,y)

```

Root (hdx,y)

```

then

```

setup (hdx)

```

that's to install the boot loader to the mbr, to install it to your linux partition

```

setup(hdx,y)

```

I used the first when I did it. Depends on what you want, but I assume you'll want the first one too

---

### Post by wilee-nilee on 2010-06-25
He has grub in the Ubuntu partition he just needs the mbr loaded and the Ubuntu partition mounted.

---

### Post by user1001 on 2010-06-25
> **wilee-nilee said:**
> He has grub in the Ubuntu partition he just needs the mbr loaded and the Ubuntu partition mounted.

So how do you do that ?
wouldn't the above answers work ? :S

---

### Post by burton247 on 2010-06-25
I bought my laptop with vista on it, first thing I did install ubuntu. Decided to upgrade to windows 7 cause I got it free through the uni, obviously re-wrote my MBR. I used my method to reinstall grub.

How do you know it is installed to the partition?

If grub was originally installed to the MBR then windows will have re-written so you'll need a re-install.

---

### Post by wilee-nilee on 2010-06-25
I think either will work, but since you had a installed Lucid the grub in lucid is not rewritten just the mbr.

---

### Post by user1001 on 2010-06-25
I typed grub at the terminal, it said I have to install it by typing so and so, I did that but it couldn't download it since there is no Internet because of the missing wireless driver, any other way I can do it?

---

### Post by philinux on 2010-06-25
> **user1001 said:**
> I typed grub at the terminal, it said I have to install it by typing so and so, I did that but it couldn't download it since there is no Internet because of the missing wireless driver, any other way I can do it?

You dont need the web for this I don't think. Maybe wired if it is needed.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Post #4 is correct too.

Post #7 refers to grub legacy and not grub2.

---

### Post by user1001 on 2010-06-25
> **philinux said:**
> You dont need the web for this I don't think. Maybe wired if it is needed.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Post #4 is correct too.

Post #7 refers to grub legacy and not grub2.

That didn't work :s

Btw I downloaded grub from windows
And I accessed it From ubuntu but when I run the files named
Install- sh nothing happens :S

---

### Post by philinux on 2010-06-25
> **user1001 said:**
> That didn't work :s

In what way? You have to be specific.

---

### Post by user1001 on 2010-06-25
> **philinux said:**
> In what way? You have to be specific.

The commands starting with # did nothing and also after one of the commands I got cp: cannot create regular file ' /Mmt/etc/ ...'
Also See my previous post, I edited it.

---

### Post by user1001 on 2010-06-25
Bump..

---

### Post by philinux on 2010-06-25
> **user1001 said:**
> Bump..

What commands starting with #? If you are not specific about what you did and any errors reported then no one can help you.

And do not bump your thread more than once on 24 hours.

See forum code of conduct.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

---

### Post by user1001 on 2010-06-25
> **philinux said:**
> What commands starting with #? If you are not specific about what you did and any errors reported then no one can help you.

And do not bump your thread more than once on 24 hours.

See forum code of conduct.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

These:
> #nano -w /etc/default/grub

Play with the options if you want.(But do not forget to give grub-update command if you saved it ;) )

Now install/recover Grub2 via :

#grub-install /dev/sda

command.However you may get errors with that code like me.If so please use this command :

#grub-install --recheck /dev/sda

these returned nothing, it just gave me a new command line :S

and I only bumped once, sorry .

---

### Post by warfacegod on 2010-06-25
Section #13: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Simplest way I know of to reinstall GRUB2.

---

### Post by user1001 on 2010-06-25
> **warfacegod said:**
> Section #13: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Simplest way I know of to reinstall GRUB2.

I tried /dev/sda6 /mnt  and I got bash permission denied

---

### Post by warfacegod on 2010-06-25
```
sudo mount /dev/sda6 /mnt/boot
```

---

### Post by wilee-nilee on 2010-06-25
Post the script in my signature in code tags. I thought there was something wrong with that original command given by the other user but I wasn't going to argue with people the bootscript will out line whats going on.

---

### Post by KEE on 2010-06-25
> **user1001 said:**
> I tried /dev/sda6 /mnt  and I got bash permission denied

I have a way its starts out like something /mbr, fdisk or FIXDISK i have to check the codes after that though. ill comeback to you later, but something you CAN'T enter in terminal or linux. you have to be in MBR to do it. I dont know if it works in dos but could try it..ill be back with the code.

---

### Post by wilee-nilee on 2010-06-25
> **KEE said:**
> I have a way its starts out like something /mbr, fdisk or FIXDISK i have to check the codes after that though. ill comeback to you later, but something you CAN'T enter in terminal or linux. you have to be in MBR to do it. I dont know if it works in dos but could try it..ill be back with the code.

[B]NO NO NO this person has to post the script at this point.
[/B]

---

### Post by user1001 on 2010-06-29
Here is my results from the boot test thing :S

---

### Post by wilee-nilee on 2010-06-29
Here is the script.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     9,979,199     9,979,137   b W95 FAT32
/dev/sda2    *      9,979,200   278,646,479   268,667,280   7 HPFS/NTFS
/dev/sda3         278,646,782   488,394,751   209,747,970   5 Extended
/dev/sda5         278,646,784   280,645,631     1,998,848  82 Linux swap / Solaris
/dev/sda6         280,647,680   488,394,751   207,747,072  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4102 MB, 4102887936 bytes
255 heads, 63 sectors/track, 498 cylinders, total 8013453 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             34     7,984,304     7,984,271   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       da5b7389-df38-0640-97c5-36caacce5917   ext2       casper-rw                     
/dev/sda1        7DD8-11A5                              vfat       HP_RECOVERY                   
/dev/sda2        6A843DF1843DBFFD                       ntfs       HP_PAVILION                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        2b45fb20-792f-47e0-971b-179fc3173f6c   swap                                     
/dev/sda6        3af816bf-c10b-4fb8-8ad5-306156116656   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D142-EAC4                              vfat       FENERLITK                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr2         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda2        /media/HP_PAVILION       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

C:\wubildr.mbr = "Ubuntu"


================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 3af816bf-c10b-4fb8-8ad5-306156116656
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 3af816bf-c10b-4fb8-8ad5-306156116656
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3af816bf-c10b-4fb8-8ad5-306156116656
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=3af816bf-c10b-4fb8-8ad5-306156116656 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3af816bf-c10b-4fb8-8ad5-306156116656
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=3af816bf-c10b-4fb8-8ad5-306156116656 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3af816bf-c10b-4fb8-8ad5-306156116656
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3af816bf-c10b-4fb8-8ad5-306156116656
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7dd8-11a5
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 22606e0d606de7cd
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 178.1GB: boot/grub/core.img
 200.2GB: boot/grub/grub.cfg
 178.3GB: boot/initrd.img-2.6.32-22-generic-pae
 178.3GB: boot/vmlinuz-2.6.32-22-generic-pae
 178.3GB: initrd.img
 178.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by wilee-nilee on 2010-06-29
So you have what looks like some of a wubi files in the windows partition sda1, is this from a install then removal of wubi or the reload or XP, the whole set which would look like this, is not there.

Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

What I do see though is this in sda1
 Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM **/wubildr.mbr /wubildr**

This can be removed from windows by typing in run msconfig and in the boot.ini just remove the wubi references.

So from the Ubuntu live cd run this.
```
sudo mount /dev/sda6 /mnt
``` Then run this
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot into Ubuntu and run in the terminal.
```
sudo update-grub
```

This should all be done if you didn't create the sda6 install from inside of windows, which from the script looks to be the case. It doesn't look like there is a wubi install still there just a couple of references in the boot.ini file in Windows, and a standard install from a live cd of Ubuntu. I wonder if the reload of XP left the wubi references in sda1

---

### Post by user1001 on 2010-06-29
> **wilee-nilee said:**
> So you have what looks like some of a wubi files in the windows partition sda1, is this from a install then removal of wubi or the reload or XP, the whole set which would look like this, is not there.

Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

What I do see though is this in sda1
 Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM **/wubildr.mbr /wubildr**

This can be removed from windows by typing in run msconfig and in the boot.ini just remove the wubi references.

So from the Ubuntu live cd run this.
```
sudo mount /dev/sda6 /mnt
``` Then run this
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot into Ubuntu and run in the terminal.
```
sudo update-grub
```

This should all be done if you didn't create the sda6 install from inside of windows, which from the script looks to be the case. It doesn't look like there is a wubi install still there just a couple of references in the boot.ini file in Windows, and a standard install from a live cd of Ubuntu. I wonder if the reload of XP left the wubi references in sda1

I installed ubuntu from a usb, not wubi, but i did download wubi and didn't use it.

so I'm confused now, how do I mount my ubuntu drive back, which is obviously still there and also how do I load the grub back too :) thanks.

---

### Post by wilee-nilee on 2010-06-29
> **wilee-nilee said:**
> So you have what looks like some of a wubi files in the windows partition sda1, is this from a install then removal of wubi or the reload or XP, the whole set which would look like this, is not there.

Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

What I do see though is this in sda1
 Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

This can be removed from windows by typing in run msconfig and in the boot.ini just remove the wubi references.

[B]So from the Ubuntu live cd run this.
```
sudo mount /dev/sda6 /mnt
``` Then run this
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot into Ubuntu and run in the terminal.
```
sudo update-grub
```[/B]



I have highlighted the process.

---

### Post by user1001 on 2010-07-01
> **wilee-nilee said:**
> I have highlighted the process.

Thank you very much, this did it =)
You are a genius. =)

Thanks to everyone who replied and helped out.

---

