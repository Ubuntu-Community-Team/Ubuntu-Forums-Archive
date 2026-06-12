---
title: "LiVE USB xHDD"
date: 2010-08-08
forum: General Help
---

### Post by TooFreppaT on 2010-08-08
[SIZE=2] can I can use the [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu") [ USB-installer]("http://en.wikipedia.org/wiki/Live_USB") as a  portable operating system (through the "try it"  feature) by selecting "[persistence]("http://en.wikipedia.org/wiki/Persistence")" when I follow the [instructions]("http://www.ubuntu.com/desktop/get-ubuntu/download") to load [/SIZE][SIZE=2]Ubuntu onto[/SIZE][SIZE=2] a bootable external hard drive
[/SIZE]

---

### Post by C.S.Cameron on 2010-08-08
Yes you can. The persistence feature will allow up to 4GB, (FAT32 size limit), you can alternatively make a persistence partition of size only limited by the size of the flash drive.

---

### Post by TooFreppaT on 2010-08-08
[LIST]
[*]I'm actually using an external (USB2.0) hard disk drive (rotating platter - not flash)
[/LIST]
 
[LIST]
[*]how do I> alternatively make a persistence partition of size only limited by the  size of the flash drive(but with an external hard disk drive?)
[/LIST]
 
[LIST]
[*] and can I do it without unplugging my internal drives? (all instructions I could find for a proper full install require this)
[/LIST]


[LIST]
[*]and does this alternative persistence partition save changes to Ubuntu? (like the default 4GB persistence)
[*]or is it just a place where you can save files to? (is it directly linked to Ubuntu - like, if you save stuff to the desktop, will it save on the  alternate persistence partition?)
[/LIST]

---

### Post by C.S.Cameron on 2010-08-08
You don't need to unplug your internal drive for persistent USB install, (you don't need to for a full install either as long as you use the "Advanced" option after partitioning and select the external drive for grub, this does put the internal drives in the external drives boot options).

Boot Live CD.
Plug in USB drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

Edit:
Dang , on second thought I can't recall if usb-creator will work with an external HDD, I do know that you can clone a persistent install from flash drive to HDD using dd and I do know that a grub2 iso boot works with a HDD:
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
Select "Discard on shutdown".
Press "Make Startup Disk.

---

### Post by TooFreppaT on 2010-08-09
how do you select the external drive for "grub" (not sure what "grub" is)
 
okay, so I have decided to do a full install (after reading your first paragraph - not sure if I'm capable of following the rest. though I did give it a go, a full install is what I would really prefer)
 
I went through the full install process (from a Live USB-FD to my USB-xHDD) and clicked on the "Advanced" option at the end of the install process - I selected my xHDD for the bootloader (not sure if this is what you mean by "grub")
 
when I boot from my USB-xHDD, it shows the following screen> GNU GRUB version 1.98-1ubuntu5
 
Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists possible
device or file completions.
 
grub> **{I then pressed TAB and the following appeared:}**
Possible commands are:
 
. 915resolution [ acpi background_image badram blocklist boot cat chainloader
clear cmp configfile cpuid crc date drivemap dump echo efiemu_loadcore efiemu_p
repare efiemu_unload exit export false functional_test gettext gptsync halt han
dler hashsum hdparm hello help hexdump initrd initrd16 insmod keystatus kfeebs
d kfreebsd_loadenv kfreebsd_module kfreebsd_module_elf knetbsd kopenbsd linux l
linux16 list_env load_env loadfront loopback ls lsfonts lsmmap lsmod lspci md5sum
module multiboot multiboot2 normal normal_exit parser.grub parser.rescue partt
ool password password_pbkdf2 play probe pxe_unload read read_byte read_dword re
ad_word reboot rmmod root save_env search search.file search.fs_label search.fs
_uuid serial set setpci sha256sum sha512sum sleep source terminal_input termina
l_output terminfo test true unset usb vbeinfo vbetest videotest write_byte writ
e_dword write_word xnu_devprop_load xnu_kernel xnu_kernel64 xnu_kext xnu_kextdi
r xnu_ramdisk xnu_resume xnu_splash xnu_uuid zfs-bootfs zfsinfo
grub>not sure if there are any typos, but I only have one computer so I had to put it all down to paper first. the text is *white* with a *black* background
 
[LEFT]any help would be awesome - as I am currently living off the same Live (persistent) USB-FD that I installed it with[/LEFT]
 
 
 
[LEFT]I also found this [http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)[/LEFT]
 
[LEFT]and this [http://pocketseo.com/scripts/43](http://pocketseo.com/scripts/43) says that I should have removed the internal drive because of something called "MBR" being written too it[/LEFT]
 
[LEFT]and I have heard this is good [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811) (#502)[/LEFT]
 
[LEFT]but I followed this [http://www.youtube.com/watch?v=eqeEsd-5_Rk&feature=related](http://www.youtube.com/watch?v=eqeEsd-5_Rk&feature=related)[/LEFT]
 
[LEFT]not sure if this is safe [http://www.youtube.com/watch?v=Fy4m6Y87WaY&feature=related](http://www.youtube.com/watch?v=Fy4m6Y87WaY&feature=related)[/LEFT]

---

### Post by oldfred on 2010-08-09
Can you manual boot, adjust ([COLOR=DarkRed]hd1,3[/COLOR]) & sdb3  or X,Y to your drive & partition?

Manual boot:
Adjust drive, partition to your install:
ls (hd[COLOR=DarkRed]1,3[/COLOR])/
sh:grub> linux (hd1,3)/vmlinuz root=/dev/sd[COLOR=DarkRed]b3[/COLOR]
sh:grub> initrd (hd1,3)/initrd.img
sh:grub> boot

Display the drives/partitions known to GRUB 2.

ls (hdX,Y)/    
Display the contents of the / folder of the designated drive/partition.

ls (hdX,Y)/boot    
Display the contents of the /boot folder. Example: ls (hd0,5)/boot

If not I would try reinstalling grub2.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

And to get grub to remember where to reinstall on updates:
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

### Post by TooFreppaT on 2010-08-09
bro, I don't know what to say

maybe I'm just getting into things that are way over my head, cos I don't understand any of that - from my perspective, it is almost as if you are speaking another language

---

### Post by oldfred on 2010-08-09
ok let's start with the liveCD.

copy & paste this command into a terminal - Applications,Accessories, terminal  (we prefer copy so we do not have to explain that the l is not 1 or I.)

```
sudo fdisk -lu
```

Paste the list of partitions back here.

---

### Post by TooFreppaT on 2010-08-09
should I have my extrenal HDD with Ubuntu installed on it plugged into the computer

this is the results without the xHDD connected
> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 4001 MB, 4001292288 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7815024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000db119

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     7358463     3678208   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2         7360510     7813119      226305    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5         7360512     7813119      226304   82  Linux swap / Solaris

Disk /dev/sdb: 8021 MB, 8021606400 bytes
5 heads, 32 sectors/track, 97920 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    15667199     7829568    b  W95 FAT32

Disk /dev/sdd: 1015 MB, 1015021568 bytes
32 heads, 61 sectors/track, 1015 cylinders, total 1982464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?   778135908  1919645538   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?   168689522  2104717761   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?  1869881465  3805909656   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdd4   ?           0  3637226495  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1863333, 7, 53)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 


---

### Post by oldfred on 2010-08-10
I wanted to see where linux was installed on your external so I could give specific commands. I do see a linux in sda1 which looks like your 4GB flash drive.

Plug in the external and rerun the command.

---

### Post by TooFreppaT on 2010-08-10
this is with the xHDD> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 4001 MB, 4001292288 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7815024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000db119

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     7358463     3678208   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2         7360510     7813119      226305    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5         7360512     7813119      226304   82  Linux swap / Solaris

Disk /dev/sdb: 8021 MB, 8021606400 bytes
5 heads, 32 sectors/track, 97920 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    15667199     7829568    b  W95 FAT32

Disk /dev/sdd: 1015 MB, 1015021568 bytes
32 heads, 61 sectors/track, 1015 cylinders, total 1982464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?   778135908  1919645538   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?   168689522  2104717761   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?  1869881465  3805909656   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdd4   ?           0  3637226495  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1863333, 7, 53)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4446

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   964743167   482370560   83  Linux
/dev/sde2       964745214   976773119     6013953    5  Extended
/dev/sde5       964745216   976773119     6013952   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 



---

### Post by oldfred on 2010-08-10
You have a linux partition in sde1, so I assume that is your Ubuntu install. Lets try reinstalling grub first. But do have have a lot of removeable devices that are sda thru sdd? 

I did have trouble getting Ubuntu to boot when I installed from one USB (sde) to another (sdf) and then removed the install USB. I did not have sdd and the install remounted at sde. So the settings were not correct and I think the search by UUID that grub does must stop looking after it finds gaps in drive letters (In my case missing sdd).

If you have unplugged any devices it may not be sde, so run fdisk and check that it shows linux on sde1.

Install MBR from LiveCD, Ubuntu install on sde1 and want grub2 in drive sde's MBR:

sudo mount /dev/sde1 /mnt
sudo grub-install --root-directory=/mnt /dev/sde
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sde

And to get grub to remember where to reinstall on updates:
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

### Post by TooFreppaT on 2010-08-11
this is what I did in Terminal
> ubuntu@ubuntu:~$ sudo mount /dev/sde1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sde
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo dpkg-reconfigure grub-pc
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
ubuntu@ubuntu:~$ 

the drive I did the full install with is the 500GB
I am running the Live USB off my 8GB
and there is a 4GB internal drive that had Ubuntu installed but I am  currently waiting to see if anyone has a solution to my problem over @  [http://ubuntuforums.org/showthread.php?t=1545125](http://ubuntuforums.org/showthread.php?t=1545125) (I originally had this  question on the same page but thought it might be better to move it  here)

---

