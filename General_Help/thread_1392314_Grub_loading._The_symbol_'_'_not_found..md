---
title: "Grub loading. The symbol ' ' not found."
date: 2010-01-27
forum: General Help
---

### Post by jonathonblake on 2010-01-27
Dell Inspiron.  (Don't know the model.)
Intel Due core 4 GB RAM
Win 7 Home Premium   64 bit 
Ubuntu 9.10 64 bit 

I'm  getting an error message of "The Symbol '' not found".
Hit any key.

Alternatively, I get an error message of "No Bootable disks found".

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/482757](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/482757)  looked promising:

> 1. Boot with LiveCD
2. Open terminal
3. sudo fdisk -l (boot partition may be the one with the asterisk)
4. sudo mkdir /media/root
5. sudo mount /dev/sdaX /media/root, where X is your mount partition (often the one with an asterisk in step 3 above). Otherwise, try all the others.
6. mount /dev/sdaX /media/root/boot

Until that point.   Mount requires root.     and /media/root/boot  is an existing folder.   (The folder in question is "Boot", not "boot", but anyway.)


> 7. Check boot by running ls /media/root/boot. If the mount is correct, you will see files like vmlinuz and memtest

And here the problem is.  As best as I can tell, vmlinuz isn't in any directory on the hard drive.

> 8. sudo grub-install --root-directory=/media/root /dev/sda --recheck


And there is  no way I'm going to that, without knowing that it is on the correct partition.  

The other thing that looked promising was MBRFix.  Except it doesn't explicitly state that it works for Windows 7.  

Before I'm asked, the output of book_info_script_049.sh was
"boot_info_script049.sh: 237: i++  not found"  repeated roughly 150 times, before I decided to kill the script.

This version of Ubuntu was installed using Wubi.   And had I realized that that was what was happening, I never would have installed it in the first place.  

At this stage of the game, all I want to do is get rid of GRUB, and Ubuntu on that laptop.   (Technically, Ubuntu should never have been installed on it in the first place.)

The Windows "Restore Operating System disk", requires Windows to be booted up on the hard drive, to do its thing. 

###

I'm well aware that the simplest solution would be to wipe windows from the drive  --- especially since the Ubuntu installation voided the warranty  etc.  However, the point of this laptop was to use some windows software that never will be able to run under WINE.

jonathon

---

### Post by meierfra. on 2010-01-28
```
: 237: i++ not found"
```

Lets see whether we can fix that error. Open the Boot Info Script  via:

```
gksudo gedit ~/Desktop/boot_info_script049.sh
```
(this assumed that the script is on your desktop, otherwise adjusts it accordingly)

Look for

```
while (! mkdir ${Folder}${i} 2>/dev/null)
    do  
      ((i++))
      wait;
    done

```
(its around line 237)

and change it do

```
[COLOR="Red"]i=0;[/COLOR]
while (! mkdir ${Folder}${i} 2>/dev/null)
    do  
    [COLOR="Red"]  i=$((i+1))[/COLOR]
      wait;
    done
```


Save the file and try running the Boot Info Script again.


Edit: That part of the script is not very important. So even if the above did not work, one can work around it.  The description of your problems is somewhat confusing, so it would be really good if we can get the script to run.

---

### Post by meierfra. on 2010-01-28
> I'm getting an error message of "The Symbol '' not found".
Hit any key.

Alternatively, I get an error message of "No Bootable disks found".

When do these errors occur.  You said you have Wubi, so do they occur when you pick Ubuntu at the Windows Boot Menu?
Are you able to boot into Windows 7?

> 1. Boot with LiveCD
2. Open terminal
3. sudo fdisk -l (boot partition may be the one with the asterisk)
4. sudo mkdir /media/root
5. sudo mount /dev/sdaX /media/root, where X is your mount partition (often the one with an asterisk in step 3 above). Otherwise, try all the others.
6. mount /dev/sdaX /media/root/boot 

Since you are using Wubi, those instruction do not apply to you.


> all I want to do is get rid of GRUB, and Ubuntu on that laptop
If you are using Wubi, you should just be able to uninstall Wubi  like any other Windows Program


> The other thing that looked promising was MBRFix. Except it doesn't explicitly state that it works for Windows 7. 
With Wubi, Grub should not be installed in the MBR so that should not help.

---

### Post by jonathonblake on 2010-01-28
> **meierfra. said:**
> When do these errors occur. 

Right at startup.
Turn on the system, and right after the Dell logo flashes, up comes:
> GRUB Loading.
The symbol  ' ' not found
Aborted. Press any key  to exit.

And upon doing that, up comes the Live CD I'm using.

>  You said you have Wubi, so do they occur when you pick Ubuntu at the Windows Boot Menu?

I don't get that far.
> Are you able to boot into Windows 7?

No. If I could, I would wipe Ubuntu from the system.

> With Wubi, Grub should not be installed in the MBR so that should not help.

That might be the theory, but it definitely is not the practice.

jonathon

---

### Post by jonathonblake on 2010-01-28
> **meierfra. said:**
> 
Save the file and try running the Boot Info Script again.

I made those changes, then ran it.

No output.

FWIW, I tried both "sudo sh boot_info_script049.sh" and "sudo boot_info_script049.sh". The latter generated an error --- "command not found".  The former produced no output at all.



jonathon

---

### Post by meierfra. on 2010-01-28
Try

```
sudo bash boot_info_script049.sh 
```

---

### Post by jonathonblake on 2010-01-28
> **meierfra. said:**
> 

```
sudo bash boot_info_script049.sh 
```

Output is 
> 
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x75349890

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   524,037,799   493,235,880   7 HPFS/NTFS
/dev/sda4         524,040,300   976,768,064   452,727,765   5 Extended
/dev/sda5         524,040,363   958,325,444   434,285,082  83 Linux
/dev/sda6         958,325,508   976,768,064    18,442,557  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1030 MB, 1030750208 bytes
16 heads, 32 sectors/track, 3932 cylinders, total 2013184 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x741cacb1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     2,013,183     2,013,152   e W95 FAT16 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8168 MB, 8168931328 bytes
39 heads, 5 sectors/track, 81820 cylinders, total 15954944 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,192    15,954,943    15,946,752   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        36F8A821F8A7DD7D                       ntfs       RECOVERY                      
/dev/sda3        9414ABD814ABBB9C                       ntfs       OS                            
/dev/sda5        cc0ccb73-4894-42ad-a10a-c6cca43908e8   ext4                                     
/dev/sda6        735d6a71-7adf-4297-bd66-47b4acda8bee   swap                                     
/dev/sdb1        0438-A6AE                              vfat       SHUTTLE                       
/dev/sdc1        6164-3631                              vfat                                     

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

aufs             /                aufs       (rw)
/dev/sr0         /cdrom           iso9660    (rw)
/dev/loop0       /rofs            squashfs   (rw)
/dev/sdc1        /media/6164-3631 vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1        /media/SHUTTLE   vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set cc0ccb73-4894-42ad-a10a-c6cca43908e8
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
	search --no-floppy --fs-uuid --set cc0ccb73-4894-42ad-a10a-c6cca43908e8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=cc0ccb73-4894-42ad-a10a-c6cca43908e8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set cc0ccb73-4894-42ad-a10a-c6cca43908e8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=cc0ccb73-4894-42ad-a10a-c6cca43908e8 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 36f8a821f8a7dd7d
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
UUID=cc0ccb73-4894-42ad-a10a-c6cca43908e8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=735d6a71-7adf-4297-bd66-47b4acda8bee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 268.3GB: boot/grub/core.img
 268.3GB: boot/grub/grub.cfg
 268.3GB: boot/initrd.img-2.6.31-14-generic
 268.3GB: boot/vmlinuz-2.6.31-14-generic
 268.3GB: initrd.img
 268.3GB: vmlinuz


jonathon

---

### Post by meierfra. on 2010-01-28
> Output
Good. I had seen the "237: i++ not found" error once before, but wasn't able to figure out what caused it.  Now I know: It happens when the script is run via "sh" rather "bash".

> This version of Ubuntu was installed using Wubi. 
I don't know what happened: You have some traces of Wubi:  "/wubildr.mbr ". But you do not have Wubi installed. Your Ubuntu on /dev/sda5 is a regular Ubuntu.


> all I want to do is get rid of GRUB, and Ubuntu on that laptop. (

Let's restore your  Windows MBR so that you can boot into Window 7:

Boot from your Ubuntu Live CD

```
sudo apt-get install lilo
```
(Ignore the message you get, just press "enter")

and then 

```
sudo lilo -M /dev/sda mbr
```


Reboot and you should boot directly into Window 7. After that, you can can delete  the Ubuntu partition if you want. But if you change your mind and would like to keep Ubuntu, just asked and I will show you how  to boot Ubuntu.

---

### Post by jonathonblake on 2010-01-28
> **meierfra. said:**
> 
Reboot and you should boot directly into Window 7. After that, you can can delete  the Ubuntu partition if you want.

It rebooted, and the first thing that popped up was a request to  make a  backup disk.

And the second thing that popped up was an error message: "Can not find some website or other."
* No asking if I want to go online. 
* No asking if the system can go online. 
* No asking to connect to the Internet.  
There is a reason why the Wireless connection to the Net is not configured. And why the Ethernet connection is unplugged.

>  But if you change your mind and would like to keep Ubuntu,

The day that functionally equivalent software for Linux is available, is the day I'll be able to replace Win7 with a real operating system.

jonathon

---

### Post by jonathonblake on 2010-03-13
> **meierfra. said:**
> Reboot and you should boot directly into Window 7. After that, you can can delete  the Ubuntu partition if you want. But if you change your mind and would like to keep Ubuntu, just asked and I will show you how  to boot Ubuntu.

I didn't delete the Ubuntu partition.

Is there a way to make this dual boot work properly?

Two months of using Win7 has convinced me that Microsoft is poor player, strutting and fretting its hour upon the stage.

jonathon

---

### Post by meierfra. on 2010-03-13
```
Is there a way to make this dual boot work properly?
```

Let's see what happens if you reinstall Grub:

Boot from the Ubuntu Live CD. Open a terminal and type:


```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

Reboot and hopefully you will get the Grub menu where you can choose between Ubuntu and Window 7


If this does not work:  Run the boot info script again and post the new RESULTS.txt.  Also  you can use the two commands from post #8 to be able to boot into Window 7  again.

---

### Post by regnaresh on 2010-04-08
worked :)

thanks

---

### Post by jonathonblake on 2010-04-09
> **meierfra said:**
> 
Let's see what happens if you reinstall Grub:

Not sure what else I did, but both the wifi and webcam work under Ubuntu.  I can dual boot, but since I locked down Win7 so it won't go online, there hasn't been much point to it.   (On the gripping hand, since I don 't know what, much less how I locked down Win7, within 90 days Win7 won't boot up, because it hasn't called home to verify that it is genuine microsoft.)

(And btw, this is a Dell Insipron 5145.)

jonathon

---

### Post by dullard on 2010-04-09
> **jonathonblake said:**
> within 90 days Win7 won't boot up, because it hasn't called home to verify that it is genuine microsoft.)


MS customer service are pretty good at sorting that sort of thing out although there's at least two possible obstacles... 1) Mention Linux and they'll wash their hands of it, and 2) the way to fix Win7 probably involves a full reinstall from the rescue partition, which means you've lost Ubuntu as a result.

But you know this I'll bet :) Hope somebody can offer more heartwarming (and better informed) advice!

---

### Post by regnaresh on 2010-04-21
hey guys,

I had a similar problem which I could solve by following the steps given in the earlier posts.
So, now im able to boot into both the OSes......but heres the problem ...every time i shut off my win7 with a hard boot or use some external storage media(except thumbdrive) and then do a normal shut down ...booting the machine next time gives this same symbol "blah blah" not found error......and then every time i use the live cd , follow the same steps and it works again...... this has happened for more than 7 times and every time i was able to make it wrk with live cd.......im fed up of doin this every time i get this error.....and want to know if their is any permanent soln to this so that I can stop it from happening again .....any update/upgrade from WIN7 or ubuntu ?????



Thanks,
Naresh


> **dullard said:**
> MS customer service are pretty good at sorting that sort of thing out although there's at least two possible obstacles... 1) Mention Linux and they'll wash their hands of it, and 2) the way to fix Win7 probably involves a full reinstall from the rescue partition, which means you've lost Ubuntu as a result.

But you know this I'll bet :) Hope somebody can offer more heartwarming (and better informed) advice!

---

