---
title: "Mounted drive name wrong"
date: 2009-09-08
forum: General Help
---

### Post by bobke on 2009-09-08
I'm working in Dapper/hda5, and I see on my desktop two drives mounted. One is named Mepis (for hda2) and the other is named Ubuntu dapper (for on hda1). The problem is that Dapper should be Edgy becuase Edgy is on hda1 (upgraded from dapper, and the name never changed). What controls the names of these drives. I thought it had to do with partition naming, but I might be wrong. Anyway I'd like to resolve this before I upgrade Dapper/hda5 to 8.04.

---

### Post by sideaway on 2009-09-08
gparted can rename partitions. However, you'll need to unmount any drive you wish to rename first.

---

### Post by Razz27 on 2009-09-08
You should be able to change the name of the drive by using gParted - a partition manager.
Find it under system -> administration -> partition editor.
If it is not installed, use 
```
sudo apt-get install gparted
```
Open up gparted, unmount the drive, right click it, and change the label :)

---

### Post by egalvan on 2009-09-08
WARNING

Older versions of gparted **WILL ERASE A PARTITION** when the LABEL is added/changed.

The version of gparted on Hardy erased a partition when I added a LABEL.
No loss to me, it was a borked install.

So be CAREFUL.

Note, the ext2 tools will set labels...
I don't recall them tho.

---

### Post by bobke on 2009-09-08
> **sideaway said:**
> gparted can rename partitions. However, you'll need to unmount any drive you wish to rename first. I wonder if this renaming will effect reboot of the system in any way, or it it might have any adverse affect during or after an  upgrade. I mean: is the name just a visual reference, or is it connected in any way with the funcion or id of the specific kernel that will change during upgrade? I don't want to mess up anything!

---

### Post by bobke on 2009-09-08
> **egalvan said:**
> WARNING

Older versions of gparted **WILL ERASE A PARTITION** when the LABEL is added/changed.

The version of gparted on Hardy erased a partition when I added a LABEL.
No loss to me, it was a borked install.

So be CAREFUL.

Note, the ext2 tools will set labels...
I don't recall them tho.Ahh, this is what I am afraid of - As I mentioned in quote from sideways post.

---

### Post by egalvan on 2009-09-09
> **bobke said:**
> ... if this renaming will effect reboot of the system in any way, or might have any adverse affect during or after an  upgrade. I mean: is the name just a visual reference, or is it connected in any way with the funcion or id of the specific kernel that will change during upgrade? I don't want to mess up anything!

No, a standard install does not use LABEL to identify the drive.

Older versions used hda/sda to identify drives/partitions.

But at least since Hardy, UUID is used to identify partitions.

So unless you have changed the identity mechanism, changing labels WILL NOT affect your boot.

and using newer versions of gparted will not result in blanked partitions....

that behavior disappeared some short time after hardy...
I don't recall the exact version of gparted that the change was effected.

personally, I use PartedMagic for all my partitioning needs.

and I use LABEL to identify my partitions...
UUID is too un-readable.

but that's me, and YMMV :)

---

### Post by bobke on 2009-09-09
> **egalvan said:**
> 

using newer versions of gparted will not result in blanked partitions....

that behavior disappeared some short time after hardy...
I don't recall the exact version of gparted that the change was effected.

personally, I use PartedMagic for all my partitioning needs.

  :)I'm upgrading from dapper to hardy the affected partition is the one I'm upgrading to, so I imagine that the name will change anyway, maybe. I have been somewhat disappointed with Gparted. How does PartedMagic compare, and is it compatible w/ gnome?

---

### Post by egalvan on 2009-09-10
> **bobke said:**
> I'm upgrading from dapper to hardy the affected partition is the one I'm upgrading to, so I imagine that the name will change anyway, maybe. I have been somewhat disappointed with Gparted. How does PartedMagic compare, and is it compatible w/ gnome?

Sorry for the delay...

First...
No, an install will not change the LABEL name of a drive.

It may change the designator, such as sda, sdb, etc.
Note that the file system software changed from using hda/sda (depending on what type of drive was attached, and how) to using sda for all drives, regardless of type or attachment.
This happened around Hardy. Around Intrepid, the change was complete.
This has to do with the core tools used by Linux, and not Ubuntu.

Next...
gparted is the engine (back-end) that almost all partition editors use.

The main difference is how often the gparted engine is updated in the particular "distro" you are using.

Hardy is a Long Term Support (LTS) which emphasizes stability. 
So except for security patch up-**dates**, the software is not up-**graded**.

PartedMagic is always on the cutting edge of gparted versions.
Its "reason for being" is partitioning, so being current is important. New file systems are added, as are features.

PartedMagic is a rather small download, compared to most other main-line distros. It's a full-featured one non-the-less.
I Like It...

gparted also has a small bootable iso, that is even smaller than PartedMagic.

These small sizes allows me to always have the latest PartedMagic and gparted iso, and burn them to CD.

---

### Post by bobke on 2009-09-11
> **egalvan said:**
> 

First...
No, an install will not change the LABEL name of a drive.

PartedMagic is always on the cutting edge of gparted versions.
Its "reason for being" is partitioning, so being current is important. New file systems are added, as are features.

PartedMagic is a rather small download, compared to most other main-line distros. It's a full-featured one non-the-less.
I Like It...
 1- So I'll be stuck with the "Dapper 6.06" LABEL for life if I don't change it. 2- I'll try PartedMagic and see what it does. The one thing that I have difficulty with gparted is designating which drive I want to mount to. I keep getting a caution diologe that I didn't establish a root partition. I find the format of gparted confusing, even after examining the man-page for it. I don't know if PartedMagic is any more user friendly.

---

### Post by egalvan on 2009-09-14
Again, sorry for the delay...
I've been pulling some 48-hour shifts...

> **bobke said:**
> 1- So I'll be stuck with the "Dapper 6.06" LABEL for life **if I don't change it**.

Yes, you will be stuck with it...
but the important part to realize is that this is **until you change it**...
*nix does not do these changes for you, because LABELS are not designed to work this way...
They are chosen by the USER, not the SYSTEM.
They are for YOUR convenience.
But YOU CAN CHANGE THEM WHEN YOU WANT... 
just use the proper tools so you do not damage and data you may have.

>  2- I'll try PartedMagic and see what it does...
I have difficulty with gparted is designating which drive I want to mount to.

Um, I don't really understand this...

Maybe you are confusing DRIVE with PARTITION.

I guess the confusion comes from the fact that
a DRIVE can be a PARTITION,
a PARTITION can be a DRIVE.

Just remember...
DRIVE usually refers to the PHYSICAL hardware.
PARTITION refers to the LOGICAL division of that hard drive.

To change which PHYSICAL DRIVE gparted is working with,
look to the top right corner.
You will see a rectangle with the selected drive...

something like this ( on MY machine, obviously yours may differ )

```
/dev/sda  (74.50 GB
```

next to the rectangle, is a set of up/down arrows.
These let you choose the PHYSICAL DRIVE.
NOTE. THIS ONLY APPLIES IF YOU HAVE MORE THAN ONE PHYSICAL DRIVE ATTACHED AND RECOGNIZED.

To change the PARTITION, highlight the partition in the graphic box, or highlight the name in the text box.

have I understood you correctly?

>  I keep getting a caution diologe that I didn't establish a root partition. 

Well, a Linux system does require a root partition...
 this is where everything branches out from...
The reason that gparted only cautions you is that it does not know if you are setting up an install, or a data partition.
gparted is simply one of the tools that the installer  uses to set up a linux file-system, and install the software.

> I find the format of gparted confusing, even after examining the man-page for it. I don't know if PartedMagic is any more user friendly.

no, PartedMagic will be no more "user-friendly"...
it's a "mini-distro" that runs gparted as it's disk partition tool.

The reason I like PartedMagic is just that....
it's a rather full distro, that makes partitioning and formating drives rather easy...
I can surf the net, or play solitaire, while it works... :)

The way I taught myself was by using an old computer, 
and playing with gparted and it's different options.
I used PartedMagic on an old HP 500Mhz machine, with a 4GB drive.
Once I was more confident, I installed a 10GB drive and tried actual installs.

---

