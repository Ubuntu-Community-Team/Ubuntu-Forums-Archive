---
title: "Partitioning for Ubuntu"
date: 2011-08-16
forum: General Help
---

### Post by romber on 2011-08-16
So I have looked and googled this and have found some results that answer my question, but I'm not sure if it is exactly what I had in mind. 

Anyways, my question is how should I partition my hard drive with only ubuntu on it. I understand I need swap and / and /home (I think), but when I run windows, I always have my partitions set up in this way:

Partition for the OS
Partition for media (music/photos/movies etc.)
Partition for downloads (all downloads go here)

I am wondering how I can partition Ubuntu correctly, but be able to also partition for the way I did in windows. 

Thanks!

---

### Post by The Cog on 2011-08-16
That's not easy. In Linux all your personal files go in your home directory. This includes your media files and your downloads. You could of course make a separate partition for your downloads or your media files, but they would be yours and not any other user's directories. If you really want to do that, I guess you could make a mount point, say /downloads (not /media - that's for CDs, USB sticks etc.) and create a separate /downloads/username sub-folder for each user, then make a symbolic link from the /home/username/Downloads to /downloads/username. I really don't see the point in doing this though. I would ask if you really need to keep your downloads and your music on separate partitions, and if the extra work in doing so is worth the effort.

---

### Post by romber on 2011-08-16
Thanks for the reply.

The only reason I really do this is just from habit. It was how I kept my computer pretty safe from viruses, but being that Linux does not have a bunch of viruses, I don't really need to keep things separate. 

Would it make it any easier if I told you I would be the only one using the computer?

---

### Post by Elfy on 2011-08-16
I have no seperate home.

I have some data partitions (including a media one) which I mount with fstab. 

Nothing to stop you doing so :)

You can also look into symlinking them to the Music /Download folders in /home if you wished.

Do these music, download partitions already exist?

---

### Post by Mark Phelps on 2011-08-16
Since Linux really mounts everything under a single filesystem, there's not a lot of value having different partitions -- other than for sharing data with other OSs.

You could consider having a separate /home partition, that will allow you to upgrade between versions of Ubuntu -- but clean installs are generally a better policy.

---

### Post by romber on 2011-08-16
None of these partitions exist yet. I am making sure I have everything in line before I do anything.

So it seems that partitioning isn't as important in Linux as it is in Windows (or the way Linux looks at partitions is significantly different) and that it might be in my best interest to just have the default partitions (swap, /, etc.)

Fyi, I am still pretty new to Linux in general, so maybe that is something else I should consider.

---

### Post by Elfy on 2011-08-16
I would keep my data seperate from my install.

Yes as Mark Phelps says everything mounts under the same file system - but if you keep all your data 'seperate' then reinstalls/upgrades will not affect that.

---

### Post by oldfred on 2011-08-16
I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)

---

### Post by romber on 2011-08-16
> **forestpiskie said:**
> I would keep my data seperate from my install.

Yes as Mark Phelps says everything mounts under the same file system - but if you keep all your data 'seperate' then reinstalls/upgrades will not affect that.


Ok, so yes, I do need to keep my data separate. With that said, would I partition like the first reply said?

---

### Post by The Cog on 2011-08-17
If it were me, I would allocate 3 partitions:
1: swap for virtual memory, perhaps 1G, or just larger than RAM for hibernating.
2: / for storing all the system files, perhaps 10G
3: /home for storing personal files - the rest of the disk.

Actually, I am in the habit of creating two "system" partitions, keeping one unused, to install the next version of the OS on to. So for instance, I have;
/ - 10G
/ - 10G (unused until next version is released)
swap - 2G
/home - rest-of-disk.

Successive versions alternate between the two / partitions, leaving me with the previous version as a fallback.

---

### Post by Elfy on 2011-08-17
> **romber said:**
> Ok, so yes, I do need to keep my data separate. With that said, would I partition like the first reply said?

This is a linux forum - you'll get as many differing replies as you care to wait for. 

You've had possibly all the different options - make a decision and fly with it - till you change your mind ;)

Of course I am sort of tied to needing seperate data partitions as they are actually different drives.

---

### Post by romber on 2011-08-17
Thanks for the replies again! I think I am going to partition like The Cog said (and others too). Seems like the best bet for me. 

Thanks again for all the help, everyone!

---

