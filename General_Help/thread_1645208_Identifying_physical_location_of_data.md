---
title: "Identifying physical location of data"
date: 2010-12-14
forum: General Help
---

### Post by vectorm12 on 2010-12-14
I've got a linux server that I haven't setup that's got a very messed up way of mounting external resources. (Both local volumes as well as network shares)

Basically I've gotta try to sort everything out and restructure the the directories as at this time the I've got network mounts scattered all over the filesystem /net /mnt /mount /usr/***/mnt and so on and so forth.

I've sorted out quite a few of them at this point using fstab to locate and relocate mounts but there are some bits of data that I need to relocate that I can't find a entry for in fstab

The system mounts / on a RAID1 Volume on two drives and has external raid enclosures connected to it which are mounted at the correct places (/mnt)

However I've found more files scattered in the /usr/***/ directory that aren't supposed to be there.
The thing about those files is that I have no idea if they are indeed located on the internal RAID1 or if the directory is mounted there and are in fact located physically on one of the external raids.

How would I go about finding out where the data is stored physically?

Naturally I haven't got the option of simply unmounting the raids to check if the files are indeed located on the internal drives or not.

---

### Post by dabl on 2010-12-14
If you know the name of a data file, but not its location, then the "locate" command would work.

If you don't know the name of the file or directory, then I dunno how you find it ....

---

### Post by vectorm12 on 2010-12-14
yeah, but this isn't a question of "locating" the file in the filesystem.

My problem is that I need to find out on which volume the files are actually on.

---

### Post by QLee on 2010-12-14
[QUOTE=vectorm12]yeah, but this isn't a question of "locating" the file in the filesystem.

My problem is that I need to find out on which volume the files are actually on.[/QUOTE]
Maybe I'm misunderstanding what you are stating but...

If you 
1.) know where in the filesystem they are located (as dabl suggested)
and you 
2.)know which mount that portion of the filesystem is on (from fstab)
why don't you know where the files are mounted?

You stated raid 1, so they are mirrored, eh?

---

### Post by dabl on 2010-12-14
> **vectorm12 said:**
> 

My problem is that I need to find out on which volume the files are actually on.

OK.  I haven't done it myself, but my thinking is that every mounted filesystem has a host device, and UUID.  If that's true, then you need use

```
sudo fdisk -lu
```

```
sudo mount
```

and 

```
sudo blkid
```

and compare them side-by-side -- it should be possible to get back to the UUID of the device on which the filesystem is mounted.  Each UUID relates to one (and only one) device.

---

