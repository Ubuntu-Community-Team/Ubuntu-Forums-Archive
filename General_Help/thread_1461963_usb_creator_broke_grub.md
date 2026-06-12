---
title: "usb creator broke grub"
date: 2010-04-24
forum: General Help
---

### Post by cgoo on 2010-04-24
**SOLVED!!!! **This was a bizarre problem with my systems bios confusing my usb wireless adapter and hard drive with one another! The solution was to unplug the adapter and reboot. 
Thanks!!!!!

Hi, I posted this on launchpad but have not received any responses so I am posting here.

                                         Hi all, I have been running a dual boot system with xp pro on one hard drive and Ubuntu 9.10 on a second hard drive, both are sata drives. I have been using this system for a few months and have been happy with it. A few days ago I decided to try to put Ubuntu 9.10 on a bootable usb, I followed the directions from help, but when I restarted my computer I could not boot from the usb device or boot from grub2. I read the grub2 documentation and tried all 3 methods of reinstalling grub from the live cd with no success. I then decided to install Lucid beta1 to a small partition on the second hard drive, when I rebooted I had grub 1.98 which recognized all three operating systems. This worked for a couple of days then again I got the error saying that the disk does not exist. I tried reinstalling grub using different methods, I even tried to use the fixmbr command on the xp disk, still no luck, now all I can do is use the live cd. I really need to get back up and running, please help.
Thanks in advance.

---

### Post by mikewhatever on 2010-04-24
What errors do you get when reinstalling Grub?

---

### Post by carl4926 on 2010-04-24
Boot the live cd and post us

```
sudo fdisk -l
```

---

### Post by -humanaut- on 2010-04-25
Did you use unetbootin? you can accidentally erase your harddrive with it.

---

### Post by carl4926 on 2010-04-25
> **-humanaut- said:**
> Did you use unetbootin? you can accidentally erase your harddrive with it.

That was what I was thinking or if he used dd
That's why I asked for fdisk -l

---

### Post by cgoo on 2010-04-25
Hi, thanks for the responses.

mikewhatever, I received no error messages while reinstalling grub but when I try to reboot I get 'no such disk exists' and the grub rescue prompt.


carl, the results of fdisk are as follows:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca63ca63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1be24052

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37706   302873142+  83  Linux
/dev/sdb2           37707       37884     1429785    5  Extended
/dev/sdb5           37707       37884     1429753+  82  Linux swap / Solaris





-humanaut-   I used the USB startup disk creator app that comes with 9.10, followed the directions in help to the letter. My hard drives have not been erased, I can access them from the live cd.

thanks

---

### Post by carl4926 on 2010-04-25
Are you installing grub to sda or sdb
And is sda or sdb first in your boot order in the BIOS?

---

### Post by cgoo on 2010-04-25
I forgot to mention that the ls command in grub rescue gives me '(hd0,0) (hd0.1) (fd0,0)' it seems that it does not recognize one of my hard drives.

---

### Post by cgoo on 2010-04-25
carl, I installed grub to sda, which is first in the boot order.

---

### Post by carl4926 on 2010-04-25
Try this method (again- carefully)

Try fixing with the Ubuntu CD


[LIST]
[*]Open a terminal and type
[/LIST]
$ sudo fdisk -l 

[LIST]
[*]Now, you need to remember which device  listed is your linux  distribution, for reference, /dev/sda1 will be  used. Now we need to  mount the filesystem to /mnt
[/LIST]
$ sudo mount /dev/sda1 /mnt


[LIST]
[*]Now mount the rest of your  devices
[/LIST]
$ sudo mount --bind /dev /mnt/dev 

[LIST]
[*]Now chroot into your  system
[/LIST]
$ sudo chroot /mnt


[LIST]
[*]When that is done you need to run **update-grub**   to create the configuration file.
[/LIST]
$ update-grub 

[LIST]
[*]To install GRUB 2 to  the MBR, next you need to run **grub-install  /dev/sda**
[/LIST]
$ grub-install /dev/sda

And your done

---

### Post by cgoo on 2010-04-25
Here is what I have, I will reboot and let you know what happens.
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca63ca63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1be24052

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37706   302873142+  83  Linux
/dev/sdb2           37707       37884     1429785    5  Extended
/dev/sdb5           37707       37884     1429753+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
root@ubuntu:/#

---

### Post by cgoo on 2010-04-25
Ok, I rebooted and I get:

GRUB loading
error: no such disk
grub rescue>_

---

### Post by carl4926 on 2010-04-25
Try this:

```
grub-install --recheck /dev/sdb
```


PS: Is it possible you previously had sdb as 1st boot device when Ubuntu was installed?

---

### Post by cgoo on 2010-04-25
sda has always been first in the boot order.

ubuntu@ubuntu:~$ grub-install --recheck /dev/sdb
grub-mkdevicemap: error: cannot open /boot/grub/device.map
ubuntu@ubuntu:~$

---

### Post by carl4926 on 2010-04-25
I have to logout now
Try google on

grub-mkdevicemap: error: cannot open /boot/grub/device.map

---

### Post by cgoo on 2010-04-25
Thanks for your help carl

---

### Post by wilee-nilee on 2010-04-25
Post this boot script, to much is still unknown.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
use the code tags to make it easier to read if you can.

---

### Post by cgoo on 2010-04-25
Thanks wilee-nilee

    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=0baaf3ec-c93e-49cf-a9a8-bded6493e5cd)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca63ca63

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,232,124   156,232,062   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1be24052

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   605,746,347   605,746,285  83 Linux
/dev/sdb2         605,746,890   608,606,459     2,859,570   5 Extended
/dev/sdb5         605,746,953   608,606,459     2,859,507  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        FE246473246430B7                       ntfs                                     
/dev/sdb1        0baaf3ec-c93e-49cf-a9a8-bded6493e5cd   ext4                                     
/dev/sdb5        1d859ed1-fb6a-40d3-a547-b876737db8af   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /mnt                     ext4       (rw)
/dev             /mnt/dev                 none       (rw,bind)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 0baaf3ec-c93e-49cf-a9a8-bded6493e5cd
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
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 0baaf3ec-c93e-49cf-a9a8-bded6493e5cd
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=0baaf3ec-c93e-49cf-a9a8-bded6493e5cd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 0baaf3ec-c93e-49cf-a9a8-bded6493e5cd
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=0baaf3ec-c93e-49cf-a9a8-bded6493e5cd ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 0baaf3ec-c93e-49cf-a9a8-bded6493e5cd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0baaf3ec-c93e-49cf-a9a8-bded6493e5cd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 0baaf3ec-c93e-49cf-a9a8-bded6493e5cd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0baaf3ec-c93e-49cf-a9a8-bded6493e5cd ro single 
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=0baaf3ec-c93e-49cf-a9a8-bded6493e5cd / ext4 errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=2c4d50a5-fcdb-4706-af37-968844f39661 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sdb1: Location of files loaded by Grub: ===================


   1.4GB: boot/grub/core.img
   8.8GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
   2.2GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
   1.1GB: boot/vmlinuz-2.6.31-20-generic
   2.2GB: initrd.img
    .6GB: initrd.img.old
   1.1GB: vmlinuz
    .5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 





It looks like for some reason usb startup disk creator installed grub on the mbr of sdb????
thanks

---

### Post by wilee-nilee on 2010-04-25
I'm not an expert in this area, but working on the side of caution it may be that if you switch sdb as the 1st boot in bios, may work. I suspect it will take more than that though. I can't tell from these bootscripts what the boot order is or if it gives that information.

---

### Post by carl4926 on 2010-04-25
Your boot order should be sda then sdb
As you see the menu is showing :** set root=(hd1,1)**

I can't just see anything out of place.. You do have grub on sda and sdb.

This is just a flying visit. I'll take a longer look later.

---

### Post by -humanaut- on 2010-04-25
> **carl4926 said:**
> Your boot order should be sda then sdb
As you see the menu is showing :** set root=(hd1,1)**

I can't just see anything out of place.. You do have grub on sda and sdb.

This is just a flying visit. I'll take a longer look later.

You seem to know more about GRUB then me take a look at the fstab doesn't look like the mount points(UUIDs) are matching up for / .

---

### Post by carl4926 on 2010-04-25
```
=> Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=[COLOR=DarkRed]0baaf3ec-c93e-49cf-a9a8-bded6493e5cd[/COLOR])/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same  drive in 
    partition #1 for /boot/grub.
``````
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set [COLOR=DarkRed] 0baaf3ec-c93e-49cf-a9a8-bded6493e5cd[/COLOR]
    linux    /boot/vmlinuz-2.6.31-20-generic  root=UUID=[COLOR=DarkRed]0baaf3ec-c93e-49cf-a9a8-bded6493e5cd[/COLOR] ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
``````
proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=[COLOR=DarkRed]0baaf3ec-c93e-49cf-a9a8-bded6493e5cd[/COLOR] / ext4 errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=2c4d50a5-fcdb-4706-af37-968844f39661 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```What do you reckon?

---

### Post by cgoo on 2010-04-26
HI again, Thanks again for your responses. It was too nice of a day yesterday to bang my head against my monitor all day so I took a nice 14 mile kayak trip down the Willamette river through the heart of Portland. Anyhow I am back at it now and I have new information. I went into the bios and set my first hard drive (hd0) to 'off', I am now able to boot. This is more of a workaround than a solution, I would be grateful if anyone has further insight as to what went wrong.
Thanks, Chris

---

### Post by cgoo on 2010-04-26
Ok, now the only way I can boot is to go into bios, turn off the first hard drive, This gives me a grub menu with ubuntu and xp. I can boot ubuntu but not xp. If I go into bios and turn on both hard drives or if I turn on only the first hard drive I get the grub rescue prompt. This is ok for the moment but I need to be able to use xp because I use autoCAD for my work. Any suggestions?
Thanks, Chris

---

### Post by carl4926 on 2010-04-26
If you pull the power on the windows drive and try booting. Does it boot to Ubuntu OK?

---

### Post by cgoo on 2010-04-27
Yes, I get some info about the bios which I was not seeing before then
'Drive 0 not found: Serial ATA, SATA-0
Strike F1 key to continue'
When I hit the F1 key grub comes up and I can boot to Ubuntu.

---

### Post by carl4926 on 2010-04-27
If you set the Ubuntu HD as first in boot order and the win HD second. Then boot, you should get grub. Then select Ubuntu.

In a terminal do

```
sudo fdisk -l
```
Post result for me

---

### Post by cgoo on 2010-04-27
The bios only has boot order by device type (cdrom, usb, internal sata hard drive, floppy, internal ide hard drive) the two sata hard drives each have the option of on or off. One thing I just noticed is that in bios when I highlight the first drive I get:

drive0: sata0
device details: unknown

When I highlight the second drive I get:

drive 1: sata2
drive details:
device id: wd500.........
capacity: 500gb
bios: this drive is controlled by the system bios
link speed: 3.0gb/s

Is it possible that I have a drive or wire that coincidentally failed at the time I made the usb disk???
I can still retrieve files from the drive and it is still recognized by fdisk. 
chris@chris-desktop:~$ sudo fdisk -l
[sudo] password for chris: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca63ca63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1be24052

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37706   302873142+  83  Linux
/dev/sdb2           37707       60801   185510587+   5  Extended
/dev/sdb5           37707       37884     1429753+  82  Linux swap / Solaris
/dev/sdb6           37885       60619   182618856   83  Linux
/dev/sdb7           60620       60801     1461883+  82  Linux swap / Solaris
chris@chris-desktop:~$ 


??????????????????????

---

### Post by carl4926 on 2010-04-27
I have to go out now.
Please tell me what motherboard this is.
I have not come across a BIOS yet that does not have settings for boot order priority.

---

### Post by cgoo on 2010-04-27
Ok you are not going to believe this but I have finally found the problem.\\:D/
After dozens of hours researching Grub2, usb startup disk creator, dell computers and everything short of black magic and countless attempts at repairing or reinstalling Grub I found an obscure post in some forum that said that the bios of the dell dimension 5150 can become 'confused' and mistake usb devices for hard drives, even when I set the hard drive as first in the boot order it thought the usb device was the hard drive. So what I did was to shut down the computer, unplug my usb wireless device (which I have been using for months), power up the computer and there it was in all it's glory..... Grub2 fully functional and able to boot everything! Even after plugging the wireless device back in Grub works fine. I really want to thank everyone who helped me out with this especially carl4926 who got me looking in the right direction.

Thanks again,
Chris

---

### Post by wilee-nilee on 2010-04-27
That is great that you got it fixed, ever stop by freegeek?

---

### Post by carl4926 on 2010-04-27
> **cgoo said:**
> Ok you are not going to believe this but I have finally found the problem.\\:D/
After dozens of hours researching Grub2, usb startup disk creator, dell computers and everything short of black magic and countless attempts at repairing or reinstalling Grub I found an obscure post in some forum that said that the bios of the dell dimension 5150 can become 'confused' and mistake usb devices for hard drives, even when I set the hard drive as first in the boot order it thought the usb device was the hard drive. So what I did was to shut down the computer, unplug my usb wireless device (which I have been using for months), power up the computer and there it was in all it's glory..... Grub2 fully functional and able to boot everything! Even after plugging the wireless device back in Grub works fine. I really want to thank everyone who helped me out with this especially carl4926 who got me looking in the right direction.

Thanks again,
Chris

Well done.
I've seen folks give up on less.

---

### Post by cgoo on 2010-04-27
Yeah carl, I hate to be beaten by a machine.
wilee-nilee, I kind of gave up on freegeek after it took 4 tries to get a hard drive that worked. Even though they all had stickers sayin "tested o.k." two gave me the the disk failure warning, and one sounded like a dentist drill, finally I ended with one that just had some bad sectors but it seems like maybe the good parts go into the machines the volunteers build for themselves. I think Green Century is another good option for Portlanders though not very conveniently located. 

carl, if you are still interested it's a Dell dimension 5150 (dm051) bios version A07.

Thanks again,
Chris

---

