---
title: "Help! my USB doesnt mount, my THESIS is on it! :("
date: 2009-07-13
forum: General Help
---

### Post by Pasdar on 2009-07-13
This morning when I wanted to use my USB stick it just didn't mount automatically like it used to. When I try it on my windows PC it asks if I want to format it or not when I click on the drive. The USB stick is either NTSC or FAT16/32, one of these three, dont remember anymore.

Formatting it is NOT an option, I need to get my thesis from it.

Result from fdisk -l:

> Disk /dev/sde: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table


I tried to mount it manually:

> **sudo mount -t vfat /dev/sde /media/USB/**
mount: wrong fs type, bad option, bad superblock on /dev/sde,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


> **dmesg | tail**
[ 1045.127798] sd 6:0:0:0: [sde] Attached SCSI removable disk
[ 1045.127906] sd 6:0:0:0: Attached scsi generic sg5 type 0
[ 1277.124567] VFS: Can't find ext4 filesystem on dev sde.
[ 1319.475420] FAT: bogus number of reserved sectors
[ 1319.475429] VFS: Can't find a valid FAT filesystem on dev sde.
[ 1325.799540] FAT: bogus number of reserved sectors
[ 1325.799546] VFS: Can't find a valid FAT filesystem on dev sde.
[ 1493.656205] FAT: Unrecognized mount option "large" or missing value
[ 1767.795301] FAT: bogus number of reserved sectors
[ 1767.795307] VFS: Can't find a valid FAT filesystem on dev sde.

What do I do? Please help... :/

---

### Post by lisati on 2009-07-13
It's unlikely to be [NTSC]("http://en.wikipedia.org/wiki/Ntsc") unless it's a video file, [NTFS]("http://en.wikipedia.org/wiki/Ntfs") or [FAT32]("http://en.wikipedia.org/wiki/Fat32#FAT32") is more likely.

---

### Post by t0p on 2009-07-13
Since you can't mount the stick in Ubuntu or Windows, I'd say it's broken.  Flash devices have a limited shelf-life - some more limited than others.  If you haven't had it long, you can probably get it replaced by the store you bought it from.  But that doesn't help you in your current predicament.

I know you don't want to hear this, but it is good advice. And maybe your tale of woe will be a cautionary tale for others.  So here goes: Back up everything! Especially something as important as a thesis.  When I was at university, I misplaced a disk with the only copy of my dissertation on it.  Luckily I found it again.  And that taught me to always back up.

Sorry.  :p

---

### Post by fballem on 2009-07-13
> **t0p said:**
> Since you can't mount the stick in Ubuntu or Windows, I'd say it's broken.  Flash devices have a limited shelf-life - some more limited than others.  If you haven't had it long, you can probably get it replaced by the store you bought it from.  But that doesn't help you in your current predicament.

I know you don't want to hear this, but it is good advice. And maybe your tale of woe will be a cautionary tale for others.  So here goes: Back up everything! Especially something as important as a thesis.  When I was at university, I misplaced a disk with the only copy of my dissertation on it.  Luckily I found it again.  And that taught me to always back up.

Sorry.  :p

Everyone learns the hard way that they must back up. In my case, I lost a manuscript with two weeks to go before publication date. I had an old hard copy that did not have all of my edits. I spent the next two weeks madly typing the old hard copy in, editing as I went, and it turned out crap. Since then, I have been religious about backups!

Sorry

---

### Post by fballem on 2009-07-13
One possible cause is that you removed the flash drive without unmounting it first. If this is the case, it may be recoverable.

I'm going on ancient memory here, but there are two things that you might want to try:

1. Turn off your computer, insert the USB stick into the computer, then turn it on and see if it is recognized on boot up. If it is, then browse it to see if it contains the files that you need.

2. If this doesn't work, and you have access to a Windows machine, then insert the drive into that machine and determine what drive letter gets assigned to it - use My Computer. Then select Start > Run > cmd. This will open up a command prompt (an old DOS-type box). Type 'chkdsk x:', where x is the drive letter of the usb stick. This may fix the usb key. When done, make sure that you safely remove the usb key.

Good luck,

---

### Post by Herman on 2009-07-13
Install GParted (Gnome Partition Editor) in Ubuntu, or boot a Ubuntu 'Desktop Live CD' which has Gnome Partition Editor in it, or use Parted Magic or GParted LiveCD.

Insert your USB flash memory stick and click 'refresh devices' in GParted.
Unplug the USB flash memory if it doesn't show up.
Plug it back in again and click 'refresh devices' again.
Keep repeating that and some time it might show up.

It doesn't make any sense to me why this seems to help, but it seems to have worked for me a couple of times when I thought one of my flash memory sticks was dead. There must be a scientific explanation for it. I imagine it might have something to do with the flash memory controller or with wear levelling or something, but I'm only guessing. Anyway, I know it sounds crazy but just try it, it won't cost you anything but some time.

---

### Post by Pasdar on 2009-07-13
The problem is that it shows the USB stick as unallocated space. I tried chdsk before, it says it doesn't check RAW disk. Which I guess means I need to format it.

What I'm going to do next is quite risky I guess but I don't really have much choice, I'm going to format the USB stick and then use recovery software to see if I can recover the document.

---

### Post by nikhilk on 2009-07-13
> **Pasdar said:**
> What I'm going to do next is quite risky I guess but I don't really have much choice, I'm going to format the USB stick and then use recovery software to see if I can recover the document.

If that is the only option left, remember to use the "Quick Format" option while formatting (I am assuming you will do it on Windows). That will just re-initialize the FAT (first few sectors) and actual data will remain unharmed.

---

### Post by timjohn7 on 2009-07-13
I've had a similar problem using a flash drive between an Ubuntu-based machine and a n XP-based one.
Plugging it into and out of the XP machine a few (3 or 4) times sorted it out... the files just appeared in File Manager after the 3rd or 4th plug in.
I wish i could offer a scientific explanation, but after "recovering" my files and saving them to a hard drive, I just "Safely Removed" or unmounted the flash drive and have done so religiously ever since.

---

### Post by eldragon on 2009-07-13
before formatting it, use dd to keep a copy of the corrupted drive. 
you then can work on the image to try and recover something.

```

$ dd -if=/dev/sde -of=~/broken_drive.img

```

for more info:
```

$ man dd

```

---

### Post by afroman10496 on 2009-07-13
are you using a alpha release? try another machine...

---

### Post by az on 2009-07-13
Do not do anything to the drive.

Image it using gddrescue and then pull files from the image.  Gddrescue can read from faulty hardware.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)


It may be that the partition table got corrupt, but the fact that the computer is detecting a drive there is promising.  Unless you do something unwise - you should *never* write to a corrupt drive on which there is data you need to get back.

---

### Post by danwood76 on 2009-07-13
You should first try and recover the data using testdisk.
It can be found in synaptic and can recover partition tables and even recover data without a partition table so its worth a look.

I'm not at my Ubuntu machine right now but I think you jsut run 'sudo testdisk' from a terminal and it will scan the drive you select and try to recover data.
Its your best bet to recover your thesis.

Just remember in the future that flash memory is very un reliable and always eventually breaks.

---

### Post by cmost on 2009-07-13
I'm sorry to say it sounds as though your USB flash drive is broken.  I really hope you made a backup!!!  Yikes!  You'd hate to lose your thesis.  :mad:

---

### Post by earthpigg on 2009-07-13
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

i have had outstanding luck with 'testdisk' and 'photorec'.

both are in the repos, but you probably want the most up to date version for the website for something as critical as this.

try _**both**_ photorec and testdisk.

dont let the name *photorec* fool you -- it works with more than just pictures.

---

### Post by jimv on 2009-07-13
Oh, this sucks.  I'm sorry for you.  Hopefully you can get an image with DD and recover some files.

I learned the hard way too that USB sticks are not always reliable, and now I keep all of my homework in Dropbox ([http://www.getdropbox.com](http://www.getdropbox.com)), which creates a folder on my computer that is automagically synced to their server, so I have local copy and a copy on their server, and any other machine I have that is running drop box.  They have clients for Linux and Windows, and you can also access your files straight from their website.

---

### Post by Spiny Norman on 2009-07-24
I feel your pain. I dont know if it would help to defrag on a windows machine (if it&#347; windows files). The police & security services have names of forensic disc analysts, might be costly but worth it?

---

### Post by thinking2loud on 2009-09-20
That dd command again:

```
$ sudo dd if=/dev/sde of=~/broken_drive.img
```

---

