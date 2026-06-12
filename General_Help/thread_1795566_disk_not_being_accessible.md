---
title: "disk not being accessible"
date: 2011-07-02
forum: General Help
---

### Post by ClientAlive on 2011-07-02
I have a fat32 disk plugged into my mobo on my desktop machine. It has no o/s installed and I'm running Ubuntu 10.04 LTS live to access and retrieve the data on that disk.

```
fdisk -l
```

shows the disk as being a Windows 95 fat32 file system disk

```
mount -l
```

Says it's mounted at "/media" Which stands to reason because that's where I mounted it.

```
gparted
```

For the life of me I could not get a clear picture of this screen (and believe me, I tried about a dozen of them). It says something about the disk being unrecognized or unrecognized type or something like that. It lists the size of the drive and other information so it see it's existance.

Even thought mount -l shows it as being mounted, nothing shows up in terminal in "/media" and it does not show up in places in Nautilus.

I was hoping to simply copy the data off the way I did with the last one. It's almost a 20 gig drive and there may not be much data on it. I'm trying to avoid imaging the drive and having to deal with the entire size of the drive in that image.

Attached are some pics.

Any ideas?

Any help would seriously be appreciated.

Thanks
-------------------

Edit:

Sorry guys, forgot pics before.

---

### Post by dFlyer on 2011-07-02
Are you 100% sure there are files on the disk? Are the files hidden? If you cd to the drive and enter ls -ahl does it so any file?

---

### Post by ClientAlive on 2011-07-02
> **dFlyer said:**
> Are you 100% sure there are files on the disk? Are the files hidden? If you cd to the drive and enter ls -ahl does it so any file?



I should add some options to ls huh. Ls -al or -ahl. Lemme try that.

---

### Post by ClientAlive on 2011-07-02
With

```
ls -la
```

All there seems to be is the two dot files.

What is strange though is that

```
mount -l
```

says at the end of the line "type unknown (rw)"

but fdisk -l shows that it is fat32

In addition, gparted says something about type unknown but does list the total size. It does not give anything for used or unused though.

I just want to be sure there isn't anything on there before I call it.

Thanks

----------------

PS: gotta run across the street for a minute. Be back in like 10.

Thanks

---

### Post by Ghost|BTFH on 2011-07-03
Just kind of curious, I'm a little busy right now (anniversary with the missus) but why aren't you using

mount -t (type) to specify the mount type?  Also, are you sure it's vfat and not ntfs, msdos or umsdos or even possibly usbfs?

There are quite a lot of options for mount, some of which may be helpful for you to have a better chance of seeing this drive.

Now personally, I like to just slap the drive onto a (connection type here) to USB adapter and plug it in letting usb handle the handshaking as it does a pretty fantastic job of it.

Let us know how it fairs.

Oh, for more options, please take a good look at mount's manpage found [here...]("http://linux.die.net/man/8/mount")

---

### Post by ClientAlive on 2011-07-03
> **Ghost|BTFH said:**
> Just kind of curious, I'm a little busy right now (anniversary with the missus) but why aren't you using

mount -t (type) to specify the mount type?  Also, are you sure it's vfat and not ntfs, msdos or umsdos or even possibly usbfs?

There are quite a lot of options for mount, some of which may be helpful for you to have a better chance of seeing this drive.

Now personally, I like to just slap the drive onto a (connection type here) to USB adapter and plug it in letting usb handle the handshaking as it does a pretty fantastic job of it.

Let us know how it fairs.

Oh, for more options, please take a good look at mount's manpage found [here...]("http://linux.die.net/man/8/mount")


Thanks. I've been having a little trouble understanding "man mount." I was looking at it several times last night and the way they wrote that thing is not easy to follow. I should prob look for some explanation on the net about it.

I got that it is fat32 from fdisk -l. That's what it claims anyhow.

I'll have to look into these things you're talking about. I'm sure it will get me further along. Thanks.

As far as a (enclusure? Is that what your were referring to?) I'd like to have one, one of these days.  :D

I'll let ya' guys know what happens. Prob try to do some more work on it in a few hrs here.

Happy Aniversary, btw. So you guys got married close to the 4th of July then. Cool beans.

ttyl

---

### Post by srs5694 on 2011-07-04
The type reported by fdisk is what's recorded in the partition table. This might or might not be an accurate reflection of the filesystem type that's actually on the partition. To probe the filesystems in partitions, you can use blkid. Either type "sudo blkid" to probe all your partitions or add a partition device filename, as in "sudo blkid /dev/sdb1", to probe a single partition. The result will look something like this:

```
$ **sudo blkid /dev/sda1**
/dev/sda1: SEC_TYPE="msdos" UUID="5CF7-C838" TYPE="vfat" LABEL="ESP"

```

This example reveals a FAT filesystem on /dev/sda1.

My suspicion -- and I emphasize that it's only a suspicion -- is that you've got an [exFAT](http://en.wikipedia.org/wiki/Exfat) filesystem on the disk. If so, the standard Ubuntu FAT drivers won't work, although I did notice that there's an [exFAT driver](http://code.google.com/p/exfat/) for [FUSE,](http://fuse.sourceforge.net/) so you could look into that. (I've never used the FUSE exFAT driver, though, so I can't do more than provide those references.)

---

### Post by ClientAlive on 2011-07-04
> **srs5694 said:**
> The type reported by fdisk is what's recorded in the partition table. This might or might not be an accurate reflection of the filesystem type that's actually on the partition. To probe the filesystems in partitions, you can use blkid. Either type "sudo blkid" to probe all your partitions or add a partition device filename, as in "sudo blkid /dev/sdb1", to probe a single partition. The result will look something like this:

```
$ **sudo blkid /dev/sda1**
/dev/sda1: SEC_TYPE="msdos" UUID="5CF7-C838" TYPE="vfat" LABEL="ESP"

```

This example reveals a FAT filesystem on /dev/sda1.

My suspicion -- and I emphasize that it's only a suspicion -- is that you've got an [exFAT](http://en.wikipedia.org/wiki/Exfat) filesystem on the disk. If so, the standard Ubuntu FAT drivers won't work, although I did notice that there's an [exFAT driver](http://code.google.com/p/exfat/) for [FUSE,](http://fuse.sourceforge.net/) so you could look into that. (I've never used the FUSE exFAT driver, though, so I can't do more than provide those references.)


Wow! Well I'm just learning all kinds of stuff here. Way cool.

I'm in the process of a disk bake on one of the other's I already harvested and then was able to get one of the machines, so far, fired up.

```

HP Pavilion 6350
A dinosaur that prob really belongs in some museum not under someone's desk.

~ RAM upgrade: 256 mb of sdram @ a lighning fast 100 Mhz!  :D

~ Disk: Quantum Bigfoot TX8.0AT weighing in at a whopping 7.49 GB
  - never seen anything like it before. It has this odd looking, huge, morphodite, card
looking thing sticking out the side of it and it makes these god awful noises when
it runs. It's been checked out pretty thoroughly though and appears to be healthy.
I think that's just how those drives sounded back then (you know, back before there
was dirt).

~ CPU: a Pentium Celeron 800 Mhz (Ooooo . . . The Glory!)  :p

~ Mobo: Don't recall the specs on this one. I do remember it was some obscure thing
and most things (like graphics and sound) are on-board.

=> Has a NIC and it works. Surfed the net for few minutes this morning.
=> Has some other weird expansion card I don't know what it is. Has a (com port?)
on it.

```


Ahh well. What can you do? Might be good for a kid to practice and learn on.

Thanks for the info srs5694. Happy 4th man.
----------------

Edit:

Got the pics up in original post. Sorry for the oversight guys.

---

### Post by Ghost|BTFH on 2011-07-04
Hey Client,

Thanks for the well wishes, yes we like to joke that we got our fireworks a day early and everyone celebrates how awesome we are the next day. :D

Just a suggestion, these are dirt cheap and they work wonders - it's a great key tool to use in what you're wanting to do. [NewEgg Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812156102&cm_re=sata_ide_usb_adapter-_-12-156-102-_-Product")

They all do about the same thing, but this one seems to be a slightly newer design which means no need for external power for sata anymore (My old one requires sata power + the data cable...boo)

Anyhow, [Google]("http://www.google.com/") is your friend to find all things you want to know but are afraid to man (because honestly, does anyone actually still read those things in CLI anymore???)

All the man pages are out there on the web, easy access.  Like [LinuxManPages.com]("http://www.linuxmanpages.com/") is a quick-easy you should keep saved as well.

Good hunting,
Ghost|BTFH

---

### Post by ClientAlive on 2011-07-04
> **Ghost|BTFH said:**
> Hey Client,

Just a suggestion, these are dirt cheap and they work wonders - it's a great key tool to use in what you're wanting to do. [NewEgg Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812156102&cm_re=sata_ide_usb_adapter-_-12-156-102-_-Product")

They all do about the same thing, but this one seems to be a slightly newer design which means no need for external power for sata anymore (My old one requires sata power + the data cable...boo)

Good hunting,
Ghost|BTFH

Wow, under $20!


> **Ghost|BTFH said:**
> 
. . . does anyone actually still read those things in CLI anymore???)

All the man pages are out there on the web, easy access.  Like [LinuxManPages.com]("http://www.linuxmanpages.com/") is a quick-easy you should keep saved as well.

Good hunting,
Ghost|BTFH

I try but they seem to not all be written by the same author. Some of them are a little challenging to follow.


> **Ghost|BTFH said:**
> Hey Client,

Thanks for the well wishes, yes we like to joke that we got our fireworks a day early and everyone celebrates how awesome we are the next day. :D

Good hunting,
Ghost|BTFH

Glad it was a good on for you. Thanks again for ev.

Jake
:D

---

