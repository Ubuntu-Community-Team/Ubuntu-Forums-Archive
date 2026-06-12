---
title: "NFTS/FAT32 - 200G USB drive"
date: 2006-03-28
forum: General Help
---

### Post by brallan on 2006-03-28
=======================
EDIT: I found out that there ARE drivers which write to NTFS, made by the reverse-engineers at [linux-ntfs.org]("http://www.linux-ntfs.org"):
Check out these in the Wiki:
[https://wiki.ubuntu.com/NTFSReadWrite]("https://wiki.ubuntu.com/NTFSReadWrite")
[https://wiki.ubuntu.com/Lkraider/NtfsFuse]("https://wiki.ubuntu.com/Lkraider/NtfsFuse")
[https://wiki.ubuntu.com/CaptiveHowTo]("https://wiki.ubuntu.com/CaptiveHowTo")

I also found out (after the fact) that the fs-drivers do not play nicely with USB drives, so I don't recommend it.
=======================
HERE is the original post:
I am tired of not being able to write from linux to my USB drive which came formatted with NTFS. 

1) I moved the data off the drive.
2) umounted the partition
3) used gparted to repartition and format it as a single 230GB FAT32 volume

I did this both as primary and extended partition, but XP did not recognize either (dignify it with a drive letter) it merely recognizes Mass Storage USB device.

Could the problem be that no file in FAT32 can be bigger than 4G? or that the size of FAT32 drives is limited? Or that XP just simply refuses to recognize a partition made by linux? Or do I need to try again using the gparted live CD?

Is there any way to have a single large partition on a USB drive that any OS can read from? Am I naive to suppose that the megalomaniacal monopolist mentality of the micro$oft malefactors would consider allowing some kind of cross-platform file system? If not, and my only alternative is FAT32, is there any way to overcome the 4G file limit? Or to hack an NTFS drive and make it writable from *nix?

i could install 

[www.fs-driver.org/](www.fs-driver.org/)

on my own machine to get XP to read/write an ext2 (ext3 as well?) partition, but what about when i want to simply bring it with me and hook it to someone else's machine?

thanks!
brian russell

---

### Post by aysiu on 2006-03-28
[QUOTE=brallan]
Could the problem be that no file in FAT32 can be bigger than 4G?[/quote] Well, if you moved all the data off the drive, then, that's not the problem. But it is true-- files can't be bigger than 4 GB on a FAT32 partition > or that the size of FAT32 drives is limited? No. > Or that XP just simply refuses to recognize a partition made by linux? Yes. Not always, but I have seen it happen. You can use XP to reformat it as FAT32 *again*, and Windows and Linux will both recognize it as FAT32.

---

### Post by brallan on 2006-03-29
the problem is that XP doesn´t
a) see the drive in any format FAT32, NTFS or ext3
b) format anything bigger than 32G in anything other than NTFS.

I am in a bit of a hurry, since I borrowed a friend's USB drive to move all of the data off and have to return it soon, so I am trying just to reformat the drive and get my data back on to it. I'd prefer FAT32 despite the file size problems if only i could get windows to see it. does anyone know of a terminal command for fdisk?

the other problem is that Ext2IFS seems to be unable to recognize the USB drive. This may be because I did not have it formatted as an ext2 drive at the time of install (I wanted to see first if it would recognize my exisitng ext3 linux partition, which it did) I'm going to try and reinstall it in XP and see if it offers me a drive letter for the USB drive...

AAAARGH! I even downloaded the gparted live CD, to no avail. It stops every time, doesn't even get to a prompt.

---

### Post by aysiu on 2006-03-29
Strictly based on my experiences, when it comes to partitioning, resizing, reformatting, etc., nothing beats [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142)--sure, it means you have to download another distro, but it's worth it.

---

### Post by brallan on 2006-03-29
I would try diskdrake if i had more time, thanks. for the meantime i am going to go to ext2 and use [ext2IFS in XP]("http://www.fs-driver.org/") to be able to see the ext2 disk. This will limit me to only being able to use this disk with my own laptop, but I can always have a CD with the program handy just in case. Uninstalling the program is one issue, that you need to reboot. The other is that if you choose a drive letter like F: or G:, it created problems when I hooked up another usb drive. I uninstalled, rebooted, reinstaled and chose drives Z and Y for my linux partitions, this seems to work well.

but thanks.if anyone has any answer as to why i couldn't get the FAT32 drive to work in XP, let me know, it's interesting. 

It would be nice to have something truly cross-platform in terms of file systems. Perhaps overcoming the difficulties of FAT32 drives in gparted is one key: formatting drives so they work well cross-platform, and then using some combination of zip archives or linkages to be able to fudge large files from some other partition.

one person merely suggested buying two external drives, one FS for each OS. This seems to me to defeat the purpose of being able to cross information between drives and also have write permissions.

---

### Post by plors on 2006-03-29
[QUOTE=brallan]
<snip>
AAAARGH! I even downloaded the gparted live CD, to no avail. It stops every time, doesn't even get to a prompt.[/QUOTE]

please [file a bug]("http://gparted.sourceforge.net/bugs.php") if you still experience this with the latest livecd.

---

### Post by frodon on 2006-03-29
brallan, how did you format your drive with gparted ?
Do you have just one primary partition ?

Could you paste the output of this command : ```
sudo fdisk -l /dev/name_of_the_drive
```The name of the drive should be something like hda, hdb, hdc, sda or something like that.

I asked you that because even if you set your partition as FAT32, if it's a logical partition what is important is the format of the extended partition.

---

### Post by Vulpus on 2006-03-29
[QUOTE=brallan]I
but thanks.if anyone has any answer as to why i couldn't get the FAT32 drive to work in XP, let me know, it's interesting. 
[/QUOTE]

I have had similar problems in XP Pro where a USB device is detected but not allocated a drive letter.  Problems can arise when you have a lot of network drives mapped with drive letters.  Part of the problem is that Windows is not very intelligent when it comes to the allocation of drive letters.  

Windows will try to allocate a drive letter to the USB device (say G) but that letter may already be allocated to a network drive.  On my laptop I have a system partition (C), data partition (D), Memory stick reader (E) and a CD-ROm (F).  When I plug in a USB device it automatically tries to allocate it the next drive letter (G).  But we have a network drive already mapped as G so it doesnt work.  

  What _should_ happen is that it allocates an unused letter but it doesnt seem to do that.  You have to manually allocate a drive letter.  Right click on the 'My Computer' icon and select MANAGE > STORAGE > DISK MANAGEMENT.  

Just for your reference I have a 60GB external HD formatted as FAT32 full of MP3s that I transfer from PC to PC.  It works with Windows ME, XP Home, XP Pro, Ubuntu and SUSE.  My only problem is on my laptop where I have had to manually allocate it the drive letter B:  So the theory is sound, you 'should' be able to do what you want.

This is yet another example of why Linux is better than Windows, no messing about with drive letters.

---

### Post by RoboJ1M on 2006-03-29
If you want to just "take it with you"

Partition it into a small FAT32 partion (128Mb or something)
And put the Win32 installer for the ext2/3 driver on there.
Then partition the rest as ext.

Maybe you could even but a whole bootable live distro on the first partition as well (just make it 1Gb).

I have no idea if that would work (Do USB Mass devices support multiple partitions)

Not a solution for your problem, just an idea for portability.

J1M.

---

### Post by brallan on 2006-03-31
> Just for your reference I have a 60GB external HD formatted as FAT32 full of MP3s that I transfer from PC to PC.  It works with Windows ME, XP Home, XP Pro, Ubuntu and SUSE.  My only problem is on my laptop where I have had to manually allocate it the drive letter B:  So the theory is sound, you 'should' be able to do what you want.

well, in the end i was in a hurry to return my friend's drive so I decided to just go with the ext2 fs, because I mainly use ubuntu, and also because I'd gotten it to work from XP on my machine. I will just keep a copy of the drivers handy if i ever need it on another machine, hopefully i will not need XP admin priveledges. It also has the advantage of not limiting filesize to under 4G.

> brallan, how did you format your drive with gparted ?
Do you have just one primary partition ? 
I tried both primary and extended options. with FAT32, no luck either time. I tried gparted and qtparted, no luck. right now its in ext2:
```

sudo fdisk -l /dev/sda1
```
returns:
```
Disk /dev/sda1: 250.0 GB, 250056705024 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk /dev/sda1 doesn't contain a valid partition table

```

i also get the follwing error when I try to umount the device (rightclicking from the desktop icon)

```
Unable to eject media
eject: unable to eject, last error: Invalid argument

```

but it seems to umount fine, in fact, as an ext2 partition, the device works great. i suppose I should change the drive to an ext3 format to include journaling when i using it in ubuntu, but i am not sure if this would create more problems than solutions as [fs-driver]("http://www.fs-driver.org/") doesn't support journaling. will something like e2fsck be run at mount on both linux and windows after a mounted unplug or a crash?

---

### Post by yota on 2006-03-31
Pay attention: your drive is /dev/sda and not /dev/sda1 (which is the first partition) so you have to type this:
```

sudo fdisk -l /dev/sda

```
to list the partitions on your usb disk.

By the way I have a 250gb external hd formatted in fat32 that I can succesfully share between linux and windows machines; I have used the CLI in this way:
[LIST=1]
[*]fdisk /dev/sda (or better cfdisk /dev/sda) and create just a primary partition of type 0B (W95 FAT32) as big as the drive
[*]mkfs.vfat -F 32 /dev/sda1
[/LIST]

Hope this helps!

---

