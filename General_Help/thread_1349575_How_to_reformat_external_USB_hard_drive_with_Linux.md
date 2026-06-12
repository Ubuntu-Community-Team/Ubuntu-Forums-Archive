---
title: "How to reformat external USB hard drive with Linux filesystem?"
date: 2009-12-08
forum: General Help
---

### Post by 0xABC123 on 2009-12-08
I just bought an external 500Gb lacie hard drive. But it has some crap preinstalled.

```

alex@alex-laptop:/media/LaCie$ tree
.
|-- [COLOR=RoyalBlue]RECYCLER[/COLOR]
|   |-- [COLOR=RoyalBlue]S-1-5-21-1078081533-413027322-682003330-1003[/COLOR]
|   |   |-- [COLOR=Lime]INFO2[/COLOR]
|   |   `-- [COLOR=Lime]desktop.ini[/COLOR]
|   `-- [COLOR=RoyalBlue]S-1-5-21-725345543-1580436667-839522115-500[/COLOR]
|       |-- [COLOR=Lime]Di1.exe[/COLOR]
|       |-- [COLOR=Lime]Di2.exe[/COLOR]
|       |-- [COLOR=Lime]INFO2[/COLOR]
|       `-- [COLOR=Lime]desktop.ini[/COLOR]
|-- [COLOR=RoyalBlue]System Volume Information[/COLOR]
|   |-- [COLOR=Lime]MountPointManagerRemoteDatabase[/COLOR]
|   |-- [COLOR=RoyalBlue]_restore{313BC069-B571-464D-8612-C7690A5190BD}[/COLOR]
|   `-- [COLOR=RoyalBlue]_restore{C43395D5-DB77-4DFF-9287-C906289B06C9}[/COLOR]
|-- [COLOR=Lime]autorun.inf[/COLOR]
`-- [COLOR=Lime]start.exe[/COLOR]

6 directories, 9 files
alex@alex-laptop:/media/LaCie$ 

```Nautilus says the hard drive is just 10Mb big!? How can I reformat it with ext3 and change it's name? (no graphical tools please)

I googled but found only threads & answers about graphical tools.

---

### Post by gordintoronto on 2009-12-08
I would use Gparted.  If you insist on using the command line, try Parted.

---

### Post by 0xABC123 on 2009-12-09
parted doesn't recognize /media/LaCie as a hard disk.
gparted doesn't allow to select anything other than sda or sdb.
mke2fs didn't work either:
```

alex@alex-laptop:~$ sudo mke2fs /media/LaCie/
mke2fs 1.41.4 (27-Jan-2009)
/media/LaCie/ is not a block special device.
Proceed anyway? (y,n) y
mke2fs: Device size reported to be zero.  Invalid partition specified, or
    partition table wasn't reread after running fdisk, due to
    a modified partition being busy and in use.  You may need to reboot
    to re-read your partition table.

alex@alex-laptop:~$ 

```

---

### Post by dcstar on 2009-12-09
> **0xABC123 said:**
> parted doesn't recognize /media/LaCie as a hard disk.
gparted doesn't allow to select anything other than sda or sdb.
mke2fs didn't work either:
```

alex@alex-laptop:~$ sudo mke2fs /media/LaCie/
mke2fs 1.41.4 (27-Jan-2009)
/media/LaCie/ is not a block special device.
Proceed anyway? (y,n) y
mke2fs: Device size reported to be zero.  Invalid partition specified, or
    partition table wasn't reread after running fdisk, due to
    a modified partition being busy and in use.  You may need to reboot
    to re-read your partition table.

alex@alex-laptop:~$ 

```

You do **not** use the mounted name, you use the /dev device.

---

### Post by 0xABC123 on 2009-12-09
/dev/sdb was the external hard drive (I didn't know that before) and one partition was mounted to /media/LaCie. So I formatted the hard drive with ext3 (partition table is gpt).

But nautilus says there's only 435Gb free space and 23.5Gb is used. But when I mount the hard disk there's no any files, not even hidden ones! How can 23.5Gb be used and where's the missing 41.5Gb?

The hard drive is supposed to be 500Gb as I stated before.

---

### Post by paradigm2 on 2009-12-09
> **0xABC123 said:**
> /dev/sdb was the external hard drive (I didn't know that before) and one partition was mounted to /media/LaCie. So I formatted the hard drive with ext3 (partition table is gpt).

But nautilus says there's only 435Gb free space and 23.5Gb is used. But when I mount the hard disk there's no any files, not even hidden ones! How can 23.5Gb be used and where's the missing 41.5Gb?

The hard drive is supposed to be 500Gb as I stated before.

I'm not 100% sure but I believe a certain percentage of space is lost in the format and also reserved for special use.  The percentage you lost is a little under 10%.

---

### Post by bumanie on 2009-12-09
There are two reasons - linux puts aside 5% of the hard drive for inodes which store basic information about files, directories etc.
The other thing is that a 500GB drive is not actually 500GB in capacity:- it is less, due to dodgy mathematics used by hard drive manufacturers. A gigabyte is 1024 cubed (bytes) when measured in binary counting. However hard drive manufacturers round that down to 1000 cubed. You can see when counting many GB's, dropping off 24 cubed per gigabyte will reduce 'claimed capacity' by quite a bit - however, most operating systems use the full binary count of 1024 cubed when looking at hard drives - so 500GB hard drive, will be about 15-20GB short of that capacity due to the mathematical tricks used. Add the 5% reserved for inodes and you will be somewhere close to the figure linux is quoting.
You probably know 1MB=1024KB - if a hard drive manufacturer was measuring it, they would say 1MB=1000KB. By the way, many ISP's use the same trick and round down ones allocated download usage via the same method.
Hope that is clear.

---

### Post by 0xABC123 on 2009-12-09
Thanks.

One last question:

If I run parted/gparted without sudo, it won't work. With sudo, I don't have permissions to write to the hard drive. How can I have all permissions without sudo?

---

### Post by bumanie on 2009-12-09
Formatting a drive to a new/different filesystem is regarded as the function of an administrator/super user. A normal user does not have the right to such things to a system. A partition must be unmounted before it can be altered via gparted - you cannot format a partition that is mounted. Whilst in the gparted GUI, right click on the partition you want to format and there should be an option to unmount the drive - obviously if one wants to do something to ones hard drive that ubuntu is on (ie shrink,increase or move etc.) it is done off a live cd - this avoids the filesystems being mounted.

---

### Post by ezsit on 2009-12-09
> If I run parted/gparted without sudo, it won't work. With sudo, I don't have permissions to write to the hard drive. How can I have all permissions without sudo?

As stated before, you need to format the drive as root or with sudo. When you plug in the USB drive ( I assume that is what you have) the drive will get mounted to a point in the filesystem, 
usually something like: /media/disk/

In order to have write access to the drive you can do, in a termnal:

sudo chown username:username /media/disk

Use your own username when issuing the **chown** command and this command will **ch**ange the **own**ership of the mount point to your username and group for the duration that it is plugged in. If you unplug the USB cable and connect it later, you will need to reissue the chown command to have write access again. Is this clear?

---

### Post by zdunham on 2009-12-09
> **bumanie said:**
> There are two reasons - linux puts aside 5% of the hard drive for inodes which store basic information about files, directories etc.
The other thing is that a 500GB drive is not actually 500GB in capacity:- it is less, due to dodgy mathematics used by hard drive manufacturers. A gigabyte is 1024 cubed (bytes) when measured in binary counting. However hard drive manufacturers round that down to 1000 cubed. You can see when counting many GB's, dropping off 24 cubed per gigabyte will reduce 'claimed capacity' by quite a bit - however, most operating systems use the full binary count of 1024 cubed when looking at hard drives - so 500GB hard drive, will be about 15-20GB short of that capacity due to the mathematical tricks used. Add the 5% reserved for inodes and you will be somewhere close to the figure linux is quoting.
You probably know 1MB=1024KB - if a hard drive manufacturer was measuring it, they would say 1MB=1000KB. By the way, many ISP's use the same trick and round down ones allocated download usage via the same method.
Hope that is clear.

I never realized what you said about the manufacturers before but it now makes sense why hard drives are never actually as big as advertised. Has anyone tried to sue for false advertising for that yet? Maybe there are no "rules" governing how you have to measure hard drive size but it seems to me that it is pretty widely excepted that 1024 is the key number in measuring space for a hard drive (1024 bytes = 1 kilobyte, 1024 kilobytes = 1 megabyte, and so on...). This takes away a large amount of advertised space with the size hard drives we use now.

---

### Post by ezsit on 2009-12-09
> Has anyone tried to sue for false advertising for that yet?

Yes. Here is a link from 2003.
[http://www.out-law.com/page-3915](http://www.out-law.com/page-3915)

However, lookup gigabyte in wikipedia and you get a better idea of why there is a discrepancy between manufacturers and consumers. The manufacturer is selling a 500 GB drive and is accurate in the description if you use the metric system of measurement. The consumer expects a binary definition of gigabyte and is therefore upset (wrongly so) when they get a drive out of the box.

---

### Post by 0xABC123 on 2009-12-10
> **ezsit said:**
> As stated before, you need to format the drive as root or with sudo. When you plug in the USB drive ( I assume that is what you have) the drive will get mounted to a point in the filesystem, 
usually something like: /media/disk/

In order to have write access to the drive you can do, in a termnal:

sudo chown username:username /media/disk

Use your own username when issuing the **chown** command and this command will **ch**ange the **own**ership of the mount point to your username and group for the duration that it is plugged in. If you unplug the USB cable and connect it later, you will need to reissue the chown command to have write access again. Is this clear?

Yes. Thanks for the replies.

---

