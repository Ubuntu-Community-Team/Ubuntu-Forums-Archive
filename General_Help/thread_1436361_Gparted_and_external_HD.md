---
title: "Gparted and external HD"
date: 2010-03-22
forum: General Help
---

### Post by TheNessus on 2010-03-22
Right, so I have a samsung external HD. I want to format it with Gparted. I get to choose what partition table to make it, i.e. msdos, aix, bsd, etc. What to choose?
Will it even run afterwards? I want to use it as ext3 or 4 basically, to store data.

---

### Post by ajgreeny on 2010-03-22
So what is the problem?  Just delete all the partitions on it at the moment, make a new partition and format it to ext3 or ext4.  No need to worry about partition tables at that stage, just let gparted make and format the new partition.

Don't forget if you should ever want to read it with a windows machine, you will not be able to, or not directly and easily, at least, if it is an ext# format partition.  You might consider having two partitions on it, ntfs and ext3 or ext4, if it might ever be needed for windows, unless a single partition is the way you feel it must be.

---

### Post by TheNessus on 2010-03-22
> **ajgreeny said:**
> So what is the problem?  Just delete all the partitions on it at the moment, make a new partition and format it to ext3 or ext4.  No need to worry about partition tables at that stage, just let gparted make and format the new partition.

Don't forget if you should ever want to read it with a windows machine, you will not be able to, or not directly and easily, at least, if it is an ext# format partition.  You might consider having two partitions on it, ntfs and ext3 or ext4, if it might ever be needed for windows, unless a single partition is the way you feel it must be.

Hmm alright, thanks. I'm just worried I might somehow screw the device. Yeah, my music and movies and pictures, things I want private; a better sense of privacy, who'll guess it's a linux FS. 

thanks for your help.

EDIT - I can't just delete the partition, it's a single NTFS but locked. I must do a whole table.

EDIT 2 - oh I need to unmount it first. ok, it worked, thanks again.

---

### Post by iNaitvad on 2010-03-22
Use MSDOS under 2TB. ;) hope it helps...

---

### Post by scouser73 on 2010-03-23
> **iNaitvad said:**
> Use MSDOS under 2TB. ;) hope it helps...
+1 for this.

---

### Post by Nevon on 2010-03-23
Speaking of filesystems, how come there's no reliable EXT3/4 driver available for Windows? The filesystem spec is open, right? So how come no one has written a complete drivers for Windows yet?

---

### Post by psusi on 2010-03-23
> **Nevon said:**
> Speaking of filesystems, how come there's no reliable EXT3/4 driver available for Windows? The filesystem spec is open, right? So how come no one has written a complete drivers for Windows yet?

There is... google is your friend.

---

### Post by Nevon on 2010-03-24
> **psusi said:**
> There is... google is your friend.

Oh I know there is one. It's just that it's horribly unstable. You'd think it would be pretty solid, but it isn't.

---

