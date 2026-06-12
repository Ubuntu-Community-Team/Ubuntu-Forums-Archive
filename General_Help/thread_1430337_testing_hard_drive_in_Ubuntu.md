---
title: "testing hard drive in Ubuntu"
date: 2010-03-15
forum: General Help
---

### Post by Gatorade on 2010-03-15
I'm trying out mint for the first time. just testing it out on the live cd.

there is something called the palimpsest Disk Utility that says my hard drive Disk failure is imminent.

I've got ubuntu installed and not having any major problems at all , how do I really know if my hard drive is in risk of imminent failure?

does Ubuntu come with a disk utility similar to the one that comes with Mint so I can run a scan and see if it gives me the same results?

one guy recommended ultimate boot cd, but I don't have that.

---

### Post by cdenley on 2010-03-15
```

sudo apt-get install gsmartcontrol
gsmartcontrol-root

```

---

### Post by john newbuntu on 2010-03-15
Mint is built on Ubuntu.  Gloria uses Jaunty and Helena uses Karmic.  Yes, Palimpset is also a part of Ubuntu.  System->admin->disk utility should open palimpset.

Run extensive tests and if you see several bad sectors, it is time for a replacement or you risk data loss.  It is hard to predict when your disk will completely fail.  But backup your data and start transitioning over to a new drive just in case.

---

### Post by DawieS on 2010-03-15
I had a similar experience with an older model hard disk, it turned out that this model has -6 bad sectors (a bit of a skewed implementation of the manufacturers warranty, meaning that you could still get 6 bad sectors, and end up with what you paid for).

Some people even reported this as a bug in **Palimpset**. I disabled this warning on that drive, and just check it about once a month. It is still running strong on -6 bad sectors.:grin:

---

### Post by Gatorade on 2010-03-16
> **cdenley said:**
> ```

sudo apt-get install gsmartcontrol
gsmartcontrol-root

```

I tried that, and it said it couldn't find the package.

---

### Post by Gatorade on 2010-03-16
> **john newbuntu said:**
> Mint is built on Ubuntu.  Gloria uses Jaunty and Helena uses Karmic.  Yes, Palimpset is also a part of Ubuntu.  System->admin->disk utility should open palimpset.

Run extensive tests and if you see several bad sectors, it is time for a replacement or you risk data loss.  It is hard to predict when your disk will completely fail.  But backup your data and start transitioning over to a new drive just in case.

I didn't see disk utility where you said to look.

---

### Post by cdenley on 2010-03-16
What version of ubuntu? Both tools were added in the most recent release (ubuntu 9.10, karmic).

---

### Post by Gatorade on 2010-03-16
oh, no wonder I couldn't find it , I'm using 9.04

---

### Post by john newbuntu on 2010-03-17
This link should help you install palimpset on Jaunty:
[http://www.webupd8.org/2009/08/how-to-install-palimpsest-disk-utility.html](http://www.webupd8.org/2009/08/how-to-install-palimpsest-disk-utility.html)

---

### Post by soltanis on 2010-03-17
OP: how big is the drive? If it is new (I assume that's what you meant by "mint") I've gotten this before.

On big drives, this tends to happen; there are one or two bad sectors on the drive. Drives are manufactured with spare sectors for exactly this reason and automatically swap them out; on high density drives they are more prevalent. It has to do with the fact that a lot of sectors are packed into a tiny space, and the read/write head misaligns. I've been told a low-level format (not the one gparted does, but I think you can do one with fdisk) will solve this problem, but I never tried.

Anyways, palimpset mistakenly thinks this is a sign of imminent drive failure. On older drives, it probably would be, but I have a brand new 1.5 TB drive that has operated for 6 months straight now that begs to differ. From what I read about bad sector reallocation, it really isn't anything to worry about so long as the number isn't steadily increasing.

Someone should probably file a bug report about that.

---

### Post by dcstar on 2010-03-17
> **soltanis said:**
> 
.........
Anyways, palimpset mistakenly thinks this is a sign of imminent drive failure. On older drives, it probably would be, but I have a brand new 1.5 TB drive that has operated for 6 months straight now that begs to differ. From what I read about bad sector reallocation, it really isn't anything to worry about so long as the number isn't steadily increasing.

Someone should probably file a bug report about that.

This has been reported for months now, if someone looks in Launchpad there will probably be (many) bug reports on it.

---

### Post by srs5694 on 2010-03-17
> **soltanis said:**
> I've been told a low-level format (not the one gparted does, but I think you can do one with fdisk) will solve this problem, but I never tried.

Linux fdisk can *not* do a low-level format on a hard disk. I don't know of any Linux utility that can. (The fdformat program will low-level format a floppy disk, but not a hard disk.) I've seen some DOS utilities that claim to be able to low-level format at least some hard disks, but I don't know if they do a true low-level format or just zero out the sectors.

History: Many moons ago (in the 1980s and maybe the early 1990s), hard disks could be low-level formatted just like floppy disks. As more and more sophisticated hard disk interfaces became available, though (increasing levels of IDE, increasing levels of SCSI, SATA, etc.), manufacturers would low-level format the drives at the factory, rendering such attention by the end user unnecessary and even dangerous, so they removed the option of doing it at all. Today, "formatting" a disk is usually synonymous with "creating a filesystem" on the disk, but that's really a high-level format, not a low-level format.

---

### Post by Gatorade on 2010-03-17
> **soltanis said:**
> OP: how big is the drive? If it is new (I assume that's what you meant by "mint") I've gotten this before.

On big drives, this tends to happen; there are one or two bad sectors on the drive. Drives are manufactured with spare sectors for exactly this reason and automatically swap them out; on high density drives they are more prevalent. It has to do with the fact that a lot of sectors are packed into a tiny space, and the read/write head misaligns. I've been told a low-level format (not the one gparted does, but I think you can do one with fdisk) will solve this problem, but I never tried.

Anyways, palimpset mistakenly thinks this is a sign of imminent drive failure. On older drives, it probably would be, but I have a brand new 1.5 TB drive that has operated for 6 months straight now that begs to differ. From what I read about bad sector reallocation, it really isn't anything to worry about so long as the number isn't steadily increasing.

Someone should probably file a bug report about that.

its a 250GB toshiba drive.

and , by mint , I was talking about linux Mint OS.

---

