---
title: "How to back-up, format the partition and then restore"
date: 2010-12-29
forum: General Help
---

### Post by New00Folder on 2010-12-29
Hi!

I've upgraded from ubuntu 9.10 to 10.04 by downloading the packages and I don't have a bootable installer CD of 10.04. Often I feel the need to re-install my OS completely (because I conduct stupid experiments). I don't want to download the packages again but I can arrange for an installer CD if needed. What I want is a way to backup all my installed programs and the several update packages so I can install them again after formatting the linux partition. It's not necessary to back up other data like music coz they're safe in a different partition.

Once I copied the contents of /var/cache/apt/archives and installed all of them after re-installing. But it left my computer confused and I kept discovering many small peculiarities for some time (things were missing from applications menu, some of the packages failed to install, wine got messed up completely, etc.). Was it a good idea?

---

### Post by howefield on 2010-12-29
Clonezilla is my favoured way of negotiating my way out of "stupid experiments" ;-)

Once you have a pristine setup, take a disk image and then use it to restore, Clonezilla will take care of formatting for you and you'll be back to square one in no time. :-).

---

### Post by audiomick on 2010-12-29
You might be looking for something like what this is supposed to do.

[http://www.ubuntugeek.com/umarks-2backup-and-restore-ubuntu-installed-packages-on-multiple-machines.html](http://www.ubuntugeek.com/umarks-2backup-and-restore-ubuntu-installed-packages-on-multiple-machines.html)

---

### Post by New00Folder on 2010-12-29
> **howefield said:**
> Clonezilla is my favoured way of negotiating my way out of "stupid experiments" ;-)

Once you have a pristine setup, take a disk image and then use it to restore, Clonezilla will take care of formatting for you and you'll be back to square one in no time. :-).
@howefield: This is how I should go. (Correct me if I'm wrong.)
Download Clonezilla live .iso and burn it to a CD to get a bootable disk.
Boot using the disk and create an image of linux partition.
Save the linux partition image somewhere safe.
When time comes boot again with Clonezilla CD and use the saved image to restore.

---

### Post by seawolf167 on 2010-12-29
> **howefield said:**
> Clonezilla is my favoured way of negotiating my way out of "stupid experiments" ;-)

Once you have a pristine setup, take a disk image and then use it to restore, Clonezilla will take care of formatting for you and you'll be back to square one in no time. :-).

+1 for Clonezilla. Just save the images to an external hard drive then restore if you mess it up or the hard drive fails.

---

### Post by howefield on 2010-12-29
> **New00Folder said:**
> @howefield: This is how I should go. (Correct me if I'm wrong.)
Download Clonezilla live .iso and burn it to a CD to get a bootable disk.
Boot using the disk and create an image of linux partition.
Save the linux partition image somewhere safe.
When time comes boot again with Clonezilla CD and use the saved image to restore.

Yep, that's pretty much it.

It looks more intimidating than it actually is, and the defaults work fine for me - so hopefully no need to mess around.

Imaging the disk (as opposed to a partition) will require another disk for the image, and will also back up the grub files.

---

### Post by New00Folder on 2010-12-29
Thanks a lot.

---

### Post by bcg30506 on 2011-02-16
> **howefield said:**
> Yep, that's pretty much it.

It looks more intimidating than it actually is, and the defaults work fine for me - so hopefully no need to mess around.

Imaging the disk (as opposed to a partition) will require another disk for the image, and will also back up the grub files.

So this means if I have 3 partitions, /, /home/, and /data (which is huge!), and just want to backup / to be able to get my OS configuration back as it was, it will not save the MBR, grub, or formatting?  How can I backup up my OS partition with Clonezilla to a USB external drive so it can be restored exactly as before, including formatting and boot up, without the time and space needed to backup hundreds of GBs of data that is already backed up my other means?

Also, if I have an XP netbook, can Clonezilla back it up, so if I then blow XP away and install an ubuntu variant and later need to put XP back on, will it successfully restore it so XP boots as if nothing happened?

Thanks.

---

### Post by New00Folder on 2011-02-16
If /data is on a different partition as you say, you don't really have to worry about backing it up pointlessly because clonezilla will create an image of only the partition which you wish it to.
You can use clonezilla to create an image of the partition with / which I think should be sufficient for your purpose if you don't change the way your disk is partitioned and formatted before you try restoring. For example you can't restore image of / on a NTFS partition.
I never had to go through with all this before but I can assure you that re-installing grub won't be a huge trouble.

Dunno if it works with Windows. But I think it's just useless to backup an image of Xp partition as since you already have all important data backed-up you can just save a copy of setups of applications, drivers, etc.  I find a freshly installed windows much better than what has been running for say a year.

---

### Post by bcg30506 on 2011-02-16
As for my Linux machine, my partitions look like:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             6.5G  2.3G  3.9G  37% /
/dev/sdb1             932G  409G  524G  44% /data
/dev/sda3             268G  144G  124G  54% /var
/dev/sda4             4.6G  2.0G  2.5G  44% /home

```
I want a backup that I can restore without manually setting everything back up if my OS drive hard crashes and I have to replace it.  This includes partitioning, formatting, and the bootloader.  I cannot seem to figure out what I need to use.

As for the XP machine, it is an EeePC that came pre-loaded with Ubuntu.  Due to my Garmin GPS software that will only run on XP (and this was years ago before VirtualBox, which now I know is a God-send), I had to put XP on it.  It has no CD drive and only 4 GB SSD for the OS.  So there are tricks I had to find and follow in order to get a "smaller" version of XP installed on this thing.  It all works, but that was several years ago and I really don't want to have to figure it out again if something goes wrong.  So far, I've been lucky.  So I want a sector by sector backup of the OS partition that I can recover from a USB disk and get the machine back in good booting condition with no fuss.

I thought I had ready Clonezilla could do this as the disksave is a sector by sector and doesn't care what the contents are.  Anyone ever tried this?

---

### Post by bcg30506 on 2011-02-16
Not tackling the big Linux server box yet, but I did cross my fingers and go ahead and give the XP netbook a shot based on some steps found via a Google search.

It works!  I first backed up via cygwin/rsync some important data files to a server, just in case.

Then I used Clonezilla Live to create 2 disk images, one of the XP boot drive and the other of my F: data drive using an external USB drive to store them and all defaults for savedisk.

Then I booted it with Ubuntu live CD (via external USB CD drive) and installed 10.04 on it.  Half way thru the install after repartitioning and formatting and starting to copy files, I turned off the machine. :)

Then I tried to boot it and of course, it wouldn't.  Got the screen saying missing OS and to insert a bootable device.  This is a good test.

So then I booted with Clonezilla again and this time chose to restoredisk from my USB hard drive.  I first chose the XP boot image and restored it using all defaults.  Once complete, I said to restart the process and did another restoredisk and this time chose the Fdrive image making sure to select the 2nd hard drive to restore to.  Once complete, I chose to reboot.

Voila!  XP came right up and all my settings, apps, documents were just as they were before.  It's as if nothing ever happened to Windows or the machine.

So good job, Clonezilla!  For what it's worth, I'm even using an older version, 20100721 of the live CD.

Now I just need answers about my Linux machine from the previous post.

---

