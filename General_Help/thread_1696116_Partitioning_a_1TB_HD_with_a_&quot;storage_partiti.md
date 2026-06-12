---
title: "Partitioning a 1TB HD with a &quot;storage partition&quot;"
date: 2011-02-26
forum: General Help
---

### Post by kelvin.illa on 2011-02-26
My last HD recently got fried, so I'm installing on a new one... (or maybe I used fsck on it because it had so many bad sectors, and now it wouldn't boot anymore).

I want to make 3/4 of the drive for general storage and the rest for the OS (10.10). It would look something like this:

```
/dev/sda...
...
...
/dev/sda(some number) ext4 750GB <--this is the storage partition
```

**I really need help setting up the partition table for the HD in the advanced partitioning tool during installation. It's 750GB for personal storage; the rest is for the OS.** I don't know how to calculate for the size of the swap. I don't know whether the storage partition should be primary or logical. I don't know about mount points. I don't know what other partitions are required for the operation of the OS.


Thanks!

---

### Post by BHEJU on 2011-02-26
I suggest following:
Three partitions
1-Swap. Size: sam as your sys ram
2-Install. size: 25 gig
3- DATA. size: rest of the remaining of 1TB.

Cheers,

---

### Post by kelvin.illa on 2011-02-26
> **BHEJU said:**
> I suggest following:
Three partitions
1-Swap. Size: sam as your sys ram
2-Install. size: 25 gig
3- DATA. size: rest of the remaining of 1TB.

Cheers,

Thanks, man (or woman). What I'm lacking, though, is the technical knowledge on how to make working partitions on the HD--particularly how to make the table.

What I need is to know for each partition are

1. Type: Primary or logical
2. Size (mostly just for the swap)
3. Location : Beginning or end
4. Use as: file system or swap (or something else)
5. Mount point: /, /boot, /home, /tmp, etc.

This is for my desktop computer.

Thanks.

---

### Post by seawolf167 on 2011-02-26
Partitions:

0. mount point: /boot
size: 200MB

1. mount point: /
size: 20GB

2. mount point: /home
size: 20GB

3. mount point: swap
size: 2GB

4. mount point: /storage
size: remainder

Mounting beginning or end doesn't matter, especially with a 1TB drive. The sector you specify can lie anywhere on the disk on a new drive, even then, with multiple platters you can never be sure where it is reading (inside or outside).

You don't have to set the mount point or even partition the storage partition during installation. Once your system is up and running you can very easily partition this unallocated space with GParted, then assign a mount point in /etc/fstab.

Partitions other than / are optional. If you don't want a /boot partition, it'll just be incorporated in /, same for /home.

You can have up to 4 primary partitions on a single drive, if you leave off the /boot partition, just format all 4 partitions as primary.

I set / and /home as 20GB simply because for a 1TB drive (931GB in reality) you aren't too concerned about running out of space, so this could save you the headache of resizing the partitions later (though I highly doubt you'll have this issue)

---

### Post by kelvin.illa on 2011-02-27
> **seawolf167 said:**
> 
Partitions:

0. mount point: /boot
size: 200MB

1. mount point: /
size: 20GB

2. mount point: /home
size: 20GB

3. mount point: swap
size: 2GB

4. mount point: /storage
size: remainder

Mounting beginning or end doesn't matter, especially with a 1TB drive. The sector you specify can lie anywhere on the disk on a new drive, even then, with multiple platters you can never be sure where it is reading (inside or outside).

You don't have to set the mount point or even partition the storage partition during installation. Once your system is up and running you can very easily partition this unallocated space with GParted, then assign a mount point in /etc/fstab.

Partitions other than / are optional. If you don't want a /boot partition, it'll just be incorporated in /, same for /home.

You can have up to 4 primary partitions on a single drive, if you leave off the /boot partition, just format all 4 partitions as primary.

I set / and /home as 20GB simply because for a 1TB drive (931GB in reality) you aren't too concerned about running out of space, so this could save you the headache of resizing the partitions later (though I highly doubt you'll have this issue)


Thanks. That clears a lot of stuff. Like you said, /boot is optional, I didn't make a partition for because I thought if something goes wrong with /boot, I probably won't know how to fix it anyway.

_This is what I've settled for:_

1. primary, 25GB, ext4, /
[INDENT]*- I chose 25GB just because it's a nice number that fits seemingly aesthetically with...*[/INDENT]

2. logical, 75GB, ext4, /home
[INDENT]*- It felt like it had to be bigger than "/" but 50GB doesn't look good (so...).*[/INDENT]

3. logical, 6GB, swap
[INDENT]*- I went with 6GB just because the default Ubuntu installation on my laptop was 6GB... I couldn't help it. I felt it had to be the same. I hate myself.*[/INDENT]

4. primary, [remainder], /mnt/archive
[INDENT]*- I think it looks tidier if this wasn't around the other "/" directories.*[/INDENT]


**Here are some of the materials I went to; this is for future reference:**

[[COLOR="Blue"]_A conversation about how some people partitioned their hard drive_[/COLOR]]("http://www.uluga.ubuntuforums.org/showthread.php?p=8431378")

[[COLOR="Blue"]_Linux Administration Made Easy Chapter 4.3: Partitioning Hard Drive(s)_[/COLOR]]("http://tldp.org/LDP/lame/LAME/linux-admin-made-easy/install-partitioning.html")

[[COLOR="blue"]_"Create a separate home partition in Ubuntu" by the psycho cat_[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")


Thanks again. My desktop's installing right now. I hope nothing breaks.

---

### Post by kelvin.illa on 2011-02-27
> **kelvin.illa said:**
> I hope nothing breaks.

Nothing broke.

---

### Post by srs5694 on 2011-02-27
It sounds like I'm too late, but I advise *against* creating a separate "storage" partition, at least on a Linux-only computer. The reason is that the whole point of /home is user data storage; thus, a separate storage partition is redundant and will only complicate matters.

Of course, there may be specific reasons for creating a separate partition for data storage of some type -- for instance, if you're running a MythTV backend on a computer that doubles as your desktop system and you want to keep your TV recordings separate from your normal user files. For general desktop use, though, there's no advantage to separate /home and data-storage partitions.

---

### Post by kelvin.illa on 2011-02-28
It's too late for me, but it's not for someone else who happens to stumble upon this.

About /home being already my storage partition, I had considered that too. It mostly comes down to the "feel" of starting over. I have no intention of wiping clean my archived files; on the other hand, I could imagine wanting to wipe clean my /home and all of its cluttered settings. The two aren't on the same level of "wanting to wipe clean." Then again, I could just delete the part of just the setting but, like I said before, it boils down to the "feel" of it.

Still, thanks for that. I'm sure this won't be my last partitioning.

---

### Post by npjoseph on 2011-03-06
does the storage partition appear as a volume in you desktop? or in your places menu? i am used to seeing ntfs partitions on my desktop. :P it's great to keep things organized. i'm planning to switch to single boot and i really don't want folders like movies, ebooks etc. cluttering up my home folder.

---

### Post by kelvin.illa on 2011-03-06
> **npjoseph said:**
> does the storage partition appear as a volume in you desktop? or in your places menu? i am used to seeing ntfs partitions on my desktop. :P it's great to keep things organized. i'm planning to switch to single boot and i really don't want folders like movies, ebooks etc. cluttering up my home folder.

You may put (mount) your storage partition anywhere you want. Mine is "/mnt/archive"--I've explained why in the previous posts. It only shows up in the /mnt directory, doesn't show up in places, so I have it bookmarked. That works, as far as I know, for all except for /media. 

Mount your partition on /media,  then it will be treated like a removable drive--the one you would see on places and on the desktop (if you let removables show on the desktop).

Just set your mount points with fstab wherever you want them. You can always re-set and go back to it whenever.

Cheers.

---

