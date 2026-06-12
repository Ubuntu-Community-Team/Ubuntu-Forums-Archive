---
title: "Mount multiple hard drives onto one folder"
date: 2009-10-13
forum: General Help
---

### Post by solidwinter on 2009-10-13
I have a server running Samba and a folder called Movies. Its filled at the moment and I'm planning to buy another terabyte today.

Is there a way to mount multiple hard drives onto one folder or similar so that's on my windows share the I'll only have one Movies folder instead two movies folders. 

Raid is a possibility, but I'd rather do this at the software level incase one hard drive fails.

:popcorn:

---

### Post by bab1 on 2009-10-13
> **solidwinter said:**
> I have a server running Samba and a folder called Movies. Its filled at the moment and I'm planning to buy another terabyte today.

Is there a way to mount multiple hard drives onto one folder or similar so that's on my windows share the I'll only have one Movies folder instead two movies folders. 

Raid is a possibility, but I'd rather do this at the software level incase one hard drive fails.

:popcorn:

You mount partitions not harddrives.  You can creat multiple mount points (directories) inside your Movies folder.  I have shares that have multiple partitions mounted.  For example, I have a share called *Samba*.  In that share is 3 partitions called: *Backup* and *Videos* and *Pictures*.

---

### Post by solidwinter on 2009-10-14
Yes, you mount partitions, that is correct ;)

I was looking for something so that all the files from both drives show up as one folder, very similar to a raid, but on the software level.

---

### Post by Baelus on 2009-10-14
Found this at [http://ubuntuforums.org/showthread.php?t=1072396]("http://ubuntuforums.org/showthread.php?t=1072396")

> **vanadium said:**
> Don't do that. Use the symlink approach instead.
You certainly cannot mount several volumes on one location: that makes no sense. If you want several volumes to act as one storage volume, your only option is raid, as JohnLM_the_Ghost already pointed out.

Symlinks give you great flexibility. You can symlink subdirectories on disk-1, disk-2, etc in one single directory, such that all items appear together in one folder. 
```

cd /home/jeroen/Media
ln -s /media/disk-1/*
ln -s /media/disk-2/*
ln -s /media/disk-3/*

```
Using symlinks, you can organize all your data within your home folder: no need to browse outside of your home or know about mount points as a user.

---

### Post by bab1 on 2009-10-14
> **solidwinter said:**
> Yes, you mount partitions, that is correct ;)

I was looking for something so that all the files from both partitions show up as one folder, very similar to a raid, but on the software level.

It sounds like you have all of your files in the same directory right now.  Unfortunately you can only mount 1 partition to a mount point.

RAID (redundant array of inexpensive disks) is used to combine physical drives.  Do you have more than 1 drive to add (mount) to your existing filesystem?  Are you looking at JBOD?  Is the folder Movies on a separate partition of its own?  Have you considered LVM?

Lots to think about.

The simplest way is to sym-link or hard-link as suggested, but there can be issues with linking too.

I'll bet that Movies is not on its own partition.  Most likely it is just a folder under /home.  If this is so, then I would move all the movie files to a temporary location(maybe tempMovies). Use the Movies folder as the mount point for the new drive (terabyte).  Then you can move all the movie files back.  Remember that when you use the Movies folder as a mount point all the files originally in the folder become non-visible to the user.  They must be moved to the folder AFTER the partition is mounted.

You can create 1 partition that covers the entire drive.  You do not need to leave the "reserved" blocks in place.  Reserved blocks are for systems disks.  The reserved section is by default 5% of the partition size.  That's 50MB on a 1TB partition.

---

### Post by Baelus on 2009-10-14
I agree. Stay simple and consolidate all the movies in one place. It'll also probably be a lot less frustrating in the future. When your system needs to change you won't have to worry about where this is mounted to that, while over here are some files with some over there...etc. That just leads to confusion and, most likely, accidentally deleted files.

---

### Post by solidwinter on 2009-10-14
I have a JBOD server, which at the moment has one 80gb for the OS, 2*500gb for misc and 2*1tb for movies.

The two terabyte drives will simple store movies. For aesthetic reasons, I want to have one folder that I can read and write too for all those movies across to the drives.

Mainly because I'd rather have a folder called "media" than having multiply folders called "media 1", "media 2".

Remembering I have samba installed and my network contains 6 other computers attached that regular access those files, would there be a way to do it through samba?

---

### Post by Baelus on 2009-10-14
I'm not sure if two partitions can share the same mount point simultaneously, using samba or otherwise. 

I would consider LVM to have 2 drives behave as 1 logical volume. For an introduction I used this:

[http://www.howtoforge.com/linux_lvm]("http://www.howtoforge.com/linux_lvm")

There may be other options, but that's what I would go for.

---

### Post by bab1 on 2009-10-14
> **solidwinter said:**
> I have a JBOD server, which at the moment has one 80gb for the OS, 2*500gb for misc and 2*1tb for movies.

What do you mean by this?  What have you combined?  JBOD is a RAID term for combining drives, not a server term,> 

The two terabyte drives will simple store movies. For aesthetic reasons, I want to have one folder that I can read and write too for all those movies across to the drives.
We have discussed a simple method of doing this in post #5.  Have you given any consideration to the practical limitations of placing all of your files in one directory?  All aesthetics aside, ease of use should be paramount.> 

Mainly because I'd rather have a folder called "media" than having multiply folders called "media 1", "media 2".
Try looking at it in a logical tree fashion.  Can you describe your intended file structure across all the drives?  What shares are you contemplating? Now is the time to think of the future (next year).  I would engineer now what I will do in the future.  What future expansion schemes have you in mind?> 

Remembering I have samba installed and my network contains 6 other computers attached that regular access those files, would there be a way to do it through samba?
Samba is only a protocol sharing files and folders, not combining folders.

---

### Post by DGortze380 on 2009-10-14
> **Baelus said:**
> I'm not sure if two partitions can share the same mount point simultaneously, using samba or otherwise. 

I would consider LVM to have 2 drives behave as 1 logical volume. For an introduction I used this:

[http://www.howtoforge.com/linux_lvm]("http://www.howtoforge.com/linux_lvm")

There may be other options, but that's what I would go for.

Agreed, LVM is what you're looking for.

---

### Post by bab1 on 2009-10-14
> **Baelus said:**
> I'm not sure if two partitions can share the same mount point simultaneously, using samba or otherwise. 

I would consider LVM to have 2 drives behave as 1 logical volume. For an introduction I used this:

[http://www.howtoforge.com/linux_lvm]("http://www.howtoforge.com/linux_lvm")

There may be other options, but that's what I would go for.

@Baelus,

You can only mount 1 partition per mount point.  When you use LVM the logical volume is considered ONE PARTITION.  And there is the rub.  With volumes you run the risk of loosing all the data when a one disk fails.

I think it is important for solidwinter to engineer the entire solution before heading to far down this road.  I may not like LVM, but it has its place.  We haven't even gotten to a backup strategy or whether quota limits are needed.

Like I said; lots to think about

---

### Post by solidwinter on 2009-10-15
What the hell bab1, over analyse much?

A JBOD server = Just a bunch of disk server. Or, a server that has a bunch of disks.

JBOD is not raid. There is no redundancy to a bunch of disks, unless they are mirroring each other, but that would be raid1

SAMBA is not for combining drives. But it could have some functionality to show two folders as one share.

__________________________________________________________

Lets not think of this solution as data management. Instead..

You have two physically separate hard drives that have similar content. Drive one is full and Drive two is half full.

These drives are shared as "Storage one" and "Storage two".

You wish you could just have one shared folder called "Storage" that Displayed all files.

Also, you must be able to add more drives after to expand on space. It dosnt have to magically work out another drive has appeared, but you must be able to configure that drive to be displayed with the rest.

How do you solve this?

---

### Post by Baelus on 2009-10-15
@bab1,

I agree that having a well thought out overview of what is needed is important. I also agree that a backup strategy is wise. My personal method would be to figure out the details of the system in a way that completes the objective, then work out a backup solution that suits that system. Again, just my point of view.

@solidwinter,

> Also, you must be able to add more drives after to expand on space. It dosnt have to magically work out another drive has appeared, but you must be able to configure that drive to be displayed with the rest.

I still consider LVM to be a good way to go. It's quite flexible when adding or removing physical drives.

That said, doing this will mean a complete overhaul of your setup and may not be worth all the effort. Using 2 folders doesn't look as neat as a single folder, but it is quick, simple and easily modified.

If it's worth it to you then go for it. And have fun with it! :)

---

### Post by bab1 on 2009-10-15
@solidwinter,

Well... Since we don't want to spend any time before jumping in, and you are good at making things up, I would say...just do it!

---

### Post by solidwinter on 2009-10-15
> **bab1 said:**
> @solidwinter,

Well... Since we don't want to spend any time before jumping in, and you are good at making things up, I would say...just do it!

what are you on about?

---

