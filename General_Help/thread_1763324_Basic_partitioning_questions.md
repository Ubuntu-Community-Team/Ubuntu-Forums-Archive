---
title: "Basic partitioning questions"
date: 2011-05-20
forum: General Help
---

### Post by shnplr on 2011-05-20
Hi,
 
I have two 250GB disks - one is fully NTFS for Windows XP
The other for Ubuntu v11.04 (say 100GB) + (150 GB NTFS - still primarily an XP user I'm afraid, I'll create the NTFS partition last so I can delete later if necessary; I understand Ubuntu can write to NTFS so I don't need to create a FAT32).
 
I'm doing basic manual partitoning for a home desktop install.
 
Let's say:
 
swap (2GB) - primary
/ (20GB) - primary (ext4)
/home (78GB) - extended/logical (ext4)
(remaining 150GB NTFS - which I assume I can create later within XP)
 
 
I've considered separate partitioning for other mount points /usr /usr/local /var /tmp /boot etc but I don't think this is necessary at this stage for how I intend to use Ubuntu.
 
So, the simple question is this: If I don't create separate partitions for the other mount points, what partition are these folders/files created in?
 
Does it put everything else in the root partition? 
If so, doesn't this theoretically impact the size needed to allocate to root partition? 
If I run out of space in root partition, will I then need to extend it? Will my system fail to boot (assuming thats the partition where the boot files/kernel are loaded)?
If I leave 150GB freespace for later will Ubuntu try to use it during install?
 
I've read threads which say things like 7GB is sufficient for root - but does this assume other mount points (folders) are in their own partition?. 
If separate partitions are NOT created for the other mount points, in which partition do these files go?
 
I'm happy to "give it a go" and if neceesary delete all the partitions, run fixmbr and retry - but I just thought I'd ask first
 
Cheers,
 
Paul

---

### Post by nothingspecial on 2011-05-20
They go in /

You'd have to install an awful lot of stuff to go over 20 gigs

20 gigs is fine.

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              15G  3.8G   10G  28% /
```

I'm only using 3.8 of 15, waste of disk space really.

---

### Post by blind2314 on 2011-05-20
> **shnplr said:**
> Hi,
 
I have two 250GB disks - one is fully NTFS for Windows XP
The other for Ubuntu v11.04 (say 100GB) + (150 GB NTFS - still primarily an XP user I'm afraid, I'll make it last so I can delete later if necessary and I understand Ubuntu can write to NTFS).
 
I'm doing basic manual partitoning for a home desktop install.
 
Let's say:
 
swap (2GB) - primary
/ (20GB) - primary (ext4)
/home (78GB) - extended/logical
 
 
I've considered the separate partitions for other mount points /usr /usr/local /var /tmp /boot etc but I don't think this is necessary for how I intend to use Ubuntu for now.
 
So, the simple question is this: If I don't create separate partitions for each mount point, what partition will these folders/files be created in?
 
Does it put everything else into the root partition? 
If so, doesn't this theoretically impact the size allocated to root partition? 
If I run out of space, will I then need to extend the root partition? Wil my system fail to boot (assuming thats where boot is loaded)
 
I've read threads which say things like 7GB is sufficient for root - but is this assume other mount points (folders) are in their own partition. So if separate partitions are NOT created for other mount points, which partition do the files go to?
 
Cheers,
 
Paul
 
For example, if you don't define /var to have its own partition, then yes, it will go under the partition with /. Everything on your system, as far as your filesystems are concerned, lives under /. So, if you don't dedicate its own partition to it, it just shares the partition that / has, and uses that space.
 
If you run out of space in /, this can be a very bad thing. However, since as a user you'll be installing all (or very nearly all, as you should) your programs and storing your files under /home, this should keep the space requirements for / low. In my experience, 20GB for / is more than enough for the average user, as long as you don't end up storing things there accidentally.

---

### Post by 3xp10r3r|X13 on 2011-05-20
You're right, they all go into root so /.

If you run out of space, it will tell you that it does so. 
 

So where is your problem? Everything is fine :)

---

### Post by lithopsian on 2011-05-20
If / runs out of space then you have many options available before the universe implodes.  Expand the partition.  Move /var, /opt, or something else onto a separate partition.  Or maybe delete all the crap :)  My / (excluding /home) is 4.4GB.

I would perhaps just make one suggestion.  /home only requires a gig or so for things like your settings and themes, maybe a gig or two for email and browser profiles.  The rest is "data", downloaded stuff, photos, etc.  You could consider putting that sort of thing on your NTFS partition since it is very likely you will want to also access it from Windows.  If this sounds like you, then maybe reduce the /home partition and leave more for your shared partition.

Since you have a lot of space, you might also leave enough unused space that you can create a whole new Ubuntu installation if you want to upgrade to a new release one day, or space between your partitions that you can easily add to them depending on which ones you end up using the most.

---

### Post by shnplr on 2011-05-20
Thanks everyone, this answer my question perfectly.
I take your point though about reducing size of /home partition.

So I'll see how this goes:

/ (20GB) Primary - ext4
/home (10GB) Logical - ext4
swap (4GB) Logical


For anyone interested I tried the "install alongside windows option" - clicked that and away it went, no quit, no are you sure - but that's cool.

The auto install on an unallocated 250GB HDD did:

/ (246GB) Primary - ext4
swap (4GB) Logical


I deleted the partitions and run FIXMBR on c:\windows as I wasn't sure if there would be a problem reinstalling Unbuntu  with the already modified MBR.  I suspect it would have been OK, or alternatively maybe I could have resized without reinstalling - the whole install only took about 10 minutes! Amazing!

---

