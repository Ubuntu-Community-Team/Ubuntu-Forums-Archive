---
title: "New EXT3 Partition on Flash Drive Mounts w Root Owner"
date: 2010-07-20
forum: General Help
---

### Post by stevo1977 on 2010-07-20
I have a flash drive that I use to sync my work- and home-computers.  Rsync has occasional issues syncing between FAT32 (which I use on my flash drive b/c it's universal) and EXT3.

I decided to create an EXT3 partition on the flash drive in an attempt to alleviate the rsync woes.  My problem is that when I create the partition using GParted, Ubuntu auto-mounts it with Root as the owner.  I had GParted check the drive, and it found no errors to repair.

One other weird thing is that the EXT3 partition shows 84.7MB being used immediately after creating the new partition.

The FAT32 partition mounts fine, is read/write, and only shows 4KB used after the new partition scheme.

I tried doing new partitions a number of times, with EXT2, EXT3, and EXT4 just to see if that mysteriously made a difference.  Each time that partition would mount w/ Root as owner.

Anyone have any ideas as to why this is happening, or have any questions that I could clarify about this process?  Thanks in advance.

Cheers,
stevo

---

### Post by Morbius1 on 2010-07-20
>  I tried doing new partitions a number of times, with EXT2, EXT3, and  EXT4 just to see if that mysteriously made a difference.  Each time that  partition would mount w/ Root as owner.Linux is doing what it was designed to do. The external EXTx directory is seen as an extension of the base root files system and as such it will mount with root as owner just as if it was a new internal linux formatted partition.

You can either take possession of the directory or grant access to everyone. Given that you are using this across computers I suppose the best thing is to open up the permissions:

Attach the drive and allow it to mount at /media/whatever. Then issue the following command:

```
sudo chmod 0777 /media/whatever
```

This will allow anyone to add or delete files / folders to that partition.

---

### Post by stevo1977 on 2010-07-21
Thanks, Morbius1.  In my searching people made it sound like chmod wouldn't work on removable drives, but it seems to have done the trick.  I appreciate your prompt and helpful response.

Cheers,
stevo

---

### Post by JustinR on 2010-07-21
If you use a different utility like System > Administration > Disk Utility there's an option to take ownership of the drive partition - which I prefer over GParted just in case thats any help to you.

---

### Post by stevo1977 on 2010-07-21
That's cool.  I have found GParted to be a better partitioning utility, but I couldn't find any 'ownership' options, so I guess the built-in Disk Utility wins on that note.  Thanks for the heads up, Justin.  Good to know for the future.

Cheers,
stevo

---

### Post by JustinR on 2010-07-21
You welcome! and Good Luck.

---

### Post by Morbius1 on 2010-07-21
> **stevo1977 said:**
> Thanks, Morbius1.  In my searching people made it sound like chmod wouldn't work on removable drives, but it seems to have done the trick.  
Cheers,
stevo
When you go out a purchase a removable drive it's normally formatted in FAT32 or possibly NTFS - both of which are Windows filesystems. You can't do a chmod or chown on a Windows filysystem .

In your case you formatted it in EXTx - a Linux filesystem where chmod and chown do work. Different filesystems with different rules.

---

