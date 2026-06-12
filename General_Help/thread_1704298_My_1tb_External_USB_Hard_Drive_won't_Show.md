---
title: "My 1tb External USB Hard Drive won't Show?"
date: 2011-03-10
forum: General Help
---

### Post by bren.roberts@gmail.com on 2011-03-10
Hi People,

I have been trying to get my 1tb External USB Hard Drive; WD External HD1021; but although I can see it in "Disk Utility" it does not appear on my Desktop as it used to and as it holds many family photographs and almost all of my music collection, some 150gb I am a little concerned.

I am using Ubuntu Meerkat on my Toshiba Laptop

Can anyone help me with this please as I have tried everything that I can by going through Google Search and as I am not a nerd I often have little to no idea what some of the suggestions are actually saying.

Any help will be gratefully accepted. Thanks in advance for any help that is forthcoming.

Bren

---

### Post by howefield on 2011-03-10
Does it appear in the Places menu ?

---

### Post by bren.roberts@gmail.com on 2011-03-10
> **howefield said:**
> Does it appear in the Places menu ?
Hi Howefield thanks for replying so fast.

Nope it don't

---

### Post by simonmoon42 on 2011-03-10
What happens when you choose the mount volume option in the disk utility?

run:

```
sudo fdisk -l
```

... and post the results.

---

### Post by bren.roberts@gmail.com on 2011-03-10
It appears to be showing my Internal Drive first and then the USB Drive.

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f781e22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11790    94703143+  83  Linux
/dev/sda2           11791       12161     2980057+   5  Extended
/dev/sda5           11791       12161     2980026   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021cc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121599   976743936    7  HPFS/NTFS

---

### Post by simonmoon42 on 2011-03-10
First run this:

```
sudo mkdir /media/external
```

This is creating a folder that we will mount the drive on.

Then run:
```
sudo mount -t ntfs-3g /dev/sdb /media/external
```

... and let me know if it shows up. If it does mount I'll show you how to auto-mount it after.

---

### Post by bren.roberts@gmail.com on 2011-03-10
It appears to be showing my Internal Drive first and then the USB Drive.

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f781e22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11790    94703143+  83  Linux
/dev/sda2           11791       12161     2980057+   5  Extended
/dev/sda5           11791       12161     2980026   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021cc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121599   976743936    7  HPFS/NTFS

---

### Post by bren.roberts@gmail.com on 2011-03-10
> **simonmoon42 said:**
> First run this:

```
sudo mkdir /media/external
```

This is creating a folder that we will mount the drive on.

Then run:
```
sudo mount -t ntfs-3g /dev/sdb /media/external
```

... and let me know if it shows up. If it does mount I'll show you how to auto-mount it after.

Cheers Simon,

All I got was this message,

sudo mount -t ntfs-3g /dev/sdb /media/external

NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by bren.roberts@gmail.com on 2011-03-10
Simon, I have just noticed that in the line your sent me "sudo mount -t ntfs-3g /dev/sdb /media/external" the /sdb part is slightly different to my printout from the Disk Utility Function

I changed this to sudo mount -t ntfs-3g /dev/sdb1 /media/external and I got this error message.


NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

Now, I am completely lost as the drive is sbd1 according to the Disk Utility and I have no idea what the valid NTFS is. I know that NTFS is a file system in the same way that FAT32 is but why it should be valid part is I don't know.

Thanks for your help to date.

---

### Post by simonmoon42 on 2011-03-10
Were you using it on a Windows PC previous to attaching it to this Ubuntu PC? And if so did you eject it properly?

---

### Post by bren.roberts@gmail.com on 2011-03-10
> **simonmoon42 said:**
> Were you using it on a Windows PC previous to attaching it to this Ubuntu PC? And if so did you eject it properly?
No, I was using it under Ubuntu 9.10. I did attempt to return o Windows XP but that was a big ****-up, Windows recognised the drive but wanted to Reformat it which meant all my stuff would be lost. So I installed Meerkat but it has never shown up except in the Disk Utility.

---

### Post by simonmoon42 on 2011-03-10
If you haven't, let's install g-parted:

```
sudo apt-get install gparted
```

Then run it. It's under System>Administration>GNOME Partition Editor. We want find the drive and make sure it is indeed sdb1.

---

### Post by bren.roberts@gmail.com on 2011-03-10
> **simonmoon42 said:**
> If you haven't, let's install g-parted:

```
sudo apt-get install gparted
```

Then run it. It's under System>Administration>GNOME Partition Editor. We want find the drive and make sure it is indeed sdb1.

Right, Under GParted it names it as /dev/sdb but in the graphic for the Partition it is named /dev/sdb1 and having 931gbUnknown with 15.47mb Unallocated.

Does this help you?

---

### Post by simonmoon42 on 2011-03-10
> **bren.roberts@gmail.com said:**
> Right, Under GParted it names it as /dev/sdb but in the graphic for the Partition it is named /dev/sdb1 and having 931gbUnknown with 15.47mb Unallocated.

Does this help you?

It seems like the partition table is corrupted. You could try testdisk and see if you can rebuild the partition table. If nothing else you can get your data off the drive, re-format the drive and restore your data. It will take a while, but it will get you back up and running. Hopefully someone who's been through this will see the thread and have pity on you. Sorry I can't be of more help to a fellow Gunner.

---

### Post by tredegar on 2011-03-10
I just want to throw in this thought:

150GB of personal data is a lot to lose.

Before you go messing with *anything* to enable you to remount the drive (on any OS), please, *please* take an image of the original drive with **dd**.

Run your recovery tools. If you mess up the recovery process, you still have the original image file to restore to the drive, & let you try again. Repeat until solved.

If you unintentionally cause further damage to the original, you may regret it.

A 1TB image is going to cost UK£60 for the hardware, and some time (maybe 2-5Hrs) to create the image, and only you can decide if your data is worth this.

---

### Post by bren.roberts@gmail.com on 2011-03-10
tredegar,

Thanks for the advice in your post. Just one point, What is dd and where do I find it on my system?

---

### Post by bren.roberts@gmail.com on 2011-03-10
Simon,

Many thanks for your advice and kind and gentle hand holding. I am thinking seriously about using a sledge hammer getting a new drive and going potty on Piratebay again. Hey Ho.

Bad night on Tuesday, and I have to put up with all the locals crowing about Barca', the price of sunny climes I suppose.

thanks again Simon.

---

### Post by tredegar on 2011-03-11
**dd** is already on your system.

It is a command line tool, to be run in a terminal.
[Here are some examples]("http://www.backuphowto.info/linux-backup-hard-disk-clone-dd") of how to use it.

---

### Post by nothingspecial on 2011-03-11
You could try ntfsfix, I doubt it would work but it's worth a shot.

```
sudo apt-get install ntfsprogs

sudo ntfsfix /dev/sdb1
```

On a side note I'd pop over to the forum feedback and help and request a username change or that email address is going to get spammed.

> Arsenal, the only Premier League team to have gone whole season undefeated and hold the record of 49 games unbeaten. 

Manchester United, the team that beat them ;)

---

### Post by bren.roberts@gmail.com on 2011-03-11
> **nothingspecial said:**
> You could try ntfsfix, I doubt it would work but it's worth a shot.

```
sudo apt-get install ntfsprogs

sudo ntfsfix /dev/sdb1
```

On a side note I'd pop over to the forum feedback and help and request a username change or that email address is going to get spammed.



Manchester United, the team that beat them ;)
Thanks for the reply nothingspecial. I tried your suggestion but I got the following, sadly:


Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

As for your final comments, ;¬)

Lets hope we get a better outcome tomorrow than we did on Tuesday. May the best team win and the ref' not be noticed.

---

### Post by rowland on 2011-03-11
If it was running correctly in Windows try to back up your data there, or on another PC. 
Maybe the problem is with the hard itself, try to back up and take it to the closest PC shop, maybe they can see whats the problem with it.
Good luck.

---

### Post by bren.roberts@gmail.com on 2011-03-12
Cheers Rowland,

It's the PC shop, a rarity in this part of Spain, or a hammer. ;¬)

---

