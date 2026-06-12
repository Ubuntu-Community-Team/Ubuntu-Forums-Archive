---
title: "Where did /windows go?"
date: 2006-06-01
forum: General Help
---

### Post by tom56 on 2006-06-01
In Breezy I automatically had a windows icon in "Computer" to acces my Windows XP partition. In Dapper it's gone, and I can't work out how to get it back. Any ideas?

---

### Post by Gomek on 2006-06-01
You didn't delete the partition, did you?  O.o  You might want to try under /media instead of /windows, perhaps?

If you can't figure it out, post the contents of your /etc/fstab here and we'll have a look-see.

---

### Post by tom56 on 2006-06-01
You misunderstand me. I did a clean install of Dapper, so I wouldn't expect my old fstab setting to be there. What I mean to say is that it wasn't detected automatically like it was in Breezy and I'm wondering if it was meant to. If not, how do I got about setting it up?

---

### Post by grendelkhan on 2006-06-01
You should run sudo mkdir /windows, then go to the Administration / Disks program, find that partition in it and then select it and mount it.  That will do the initial set up, but you will still need to add it to your fstab.  Unless you mounted it during the set up, you probably won't get a spot for it autocreated.  The only distro I've seen do this for you was SuSE.

---

### Post by tom56 on 2006-06-01
Well, that sorted it. It's a shame there isn't an easier way to do this though; coming from Mandrake->Gentoo->Breezy->Dapper I am quite comfortable editing fstab by hand, but I'm sure there are those who aren't. Maybe something for Eft... :)

---

### Post by Gomek on 2006-06-01
Yeah, I've always done manual partitioning, so my Windows partitions are always exactly what and where I want them to be.  The reason I mentioned that they might be under /media is that is where the manual partitioner wants to mount them by default...

But yeah, I have no clue if the automatic partitioning mounts the Windows directories by default at all.

---

### Post by tom56 on 2006-06-01
Well I did manual partioning but it didn't offer me a mountpoint and didn't make one itself.

---

### Post by Gomek on 2006-06-01
Did you use the alternate install CD or the desktop CD?

---

### Post by grendelkhan on 2006-06-01
[QUOTE=tom56]Well I did manual partioning but it didn't offer me a mountpoint and didn't make one itself.[/QUOTE]
I think that's the key.  When I did manual partitioning, I had to mount my other disks by hand and create the mount points for them.  I just plugged in the location and the installer made sure to create the directories and mount them.  What I don't know is if the installer will let you mount NTFS or FAT32 drives during the partitioning stage.

---

### Post by Gomek on 2006-06-01
It does.  I have a vfat Windows XP partition and two more vfat partitions that were automatically mounted by Ubuntu after my installation.  I used the alternate install CD and manually changed the mount points to /windows/C, /windows/D, and /windows/E during the manual partitioning phase.

---

