---
title: "Hard Drive showing as full when not?"
date: 2009-07-12
forum: General Help
---

### Post by IAmNotAUser on 2009-07-12
I'm not sure whether this truly belongs in the Hardware and Laptops section, so I'm putting it in here as a mater of organisation.

About this time last year, I built a cheap box to house a few of my spare hard drives and create a dedicated media server. At the time, I was new to Linux and followed [this online guide]("http://www.linuxjournal.com/node/1005985"), which recommended using Kubuntu for the distro as it came with VNC support out the box, which appealed to me.

After coming home from university for summer, I've attempted to copy across some files via the network onto the Kubuntu machine, but keep being greeted by out of space errors.

As I was then new to Linux, I may have messed something up during install, but I've been using it for my degree all year, and I can't now find out where the problem lies; I don't think I'm simply out of space.

For example:

I have a 500Gb HD mounted as /mnt/Backups. I know I will not get the full 500Gb storage due to partition tables and the like.
In Dolphin, the folder /mnt/Backups shows as 442.6GB in size with Free Disk Space as 268.0Mb of 462.1Gb (100% used)
In GParted, the same HD shows as 465.76GiB, Used 446.87GiB, Unused 18.89GiB.

GParted seems to be showing the values I would expect from my data as I'm copying directly from a 500Gb external that is holding the data. This also happens on a second harddrive mounted at /mnt/Backup2 with the same files, at a different value.

Both disks only have a single partition showing in GParted, mounted or unmounted.

Why can I not paste it in Dolphin? I've tried to cover all the information I think is necessary, if there's anything else you need, feel free to ask.

---

### Post by earthpigg on 2009-07-12
let's see what the command line tells us. please post the output of:

df -h /mnt/Backups

---

### Post by IAmNotAUser on 2009-07-12
Not on the machine directly as it doesn't have net connection but:

Filesystem: /dev/sdc2
Size: 463G
Used: 444G
Avail: 443M
Use%: 100%
Mounted on: /mnt/Backup

---

### Post by earthpigg on 2009-07-12
let's try to locate the trash on that external drive in the command line, and see if that needs to be emptied.

for me to see the trash on my external hard drive:

```
ep@ep-9:/media/disk$ ls -a /media/disk
.                          cli.txt          Storage
..                         cli.txt~         System Volume Information
backup date.txt            home backup      _.Trash-1000_
backup date.txt~           Incomplete       Video
Bookmarks 2009-05-16.json  
ep@ep-9:/media/disk$ 
```

then, to remove it:

```
rm -r /media/disk/.Trash-1000
```

you will have to switch things up a bit, of course, to make it work for you.

run df -h again to see if that did it.

---

### Post by blueridgedog on 2009-07-12
5% of an extn drive is reserved for root and therefore drives show up as full when there is space left.

---

### Post by IAmNotAUser on 2009-07-12
> **blueridgedog said:**
> 5% of an extn drive is reserved for root and therefore drives show up as full when there is space left.

This is an internal Hard drive though... Is the same true then? And is there any way to remove that reservation?

@earthpigg I removed the .Trash file that was there under ls -a, but still exactly the same values in df -h

---

### Post by blueridgedog on 2009-07-12
"extn" was shorthand for ext2, ext3 and ext4 formated drives, internal or external.  So, yes, it applies to all drives formated with Linux file systems.

---

### Post by IAmNotAUser on 2009-07-13
Ahh. Ok. I thought it was short for external. Sorry.

Is there any way to cancel that setting or remove that reservation on this particular drive?

---

### Post by blueridgedog on 2009-07-13
tune2fs can do it:

```
sudo tune2fs -r count device
```

For example:

```
sudo tune2fs -r 0 /dev/sdc1
```

Do not remove the reserved block on any drive mounted as /

---

### Post by theozzlives on 2009-07-13
If you deleted files as root, you may have .Trash folders everywhere.

---

### Post by IAmNotAUser on 2009-07-22
> **blueridgedog said:**
> tune2fs can do it:

```
sudo tune2fs -r count device
```For example:

```
sudo tune2fs -r 0 /dev/sdc1
```Do not remove the reserved block on any drive mounted as /

I receive the following message when I do the code above with sdc2:

tune2fs: Permission denied while trying to open /dev/sdc2
Couldn't find valid filesystem superblock.


> **theozzlives said:**
> If you deleted files as root, you may have .Trash folders everywhere.

I don't see any others anywhere that will be preventing that single drive, all the files are loose inside the directory.

---

### Post by IAmNotAUser on 2009-07-22
I was trying to run tune2fs while the drive was mounted. After reading the man page, I unmounted the drive, and the problem has been solved.

Dolphin now shows 19gb free, just like Gparted does.

Many thanks for your help.

---

### Post by dk06 on 2009-07-22
> **IAmNotAUser said:**
> I was trying to run tune2fs while the drive was mounted. After reading the man page, I unmounted the drive, and the problem has been solved.

Dolphin now shows 19gb free, just like Gparted does.

Many thanks for your help.

You must have not been a user ;)

---

