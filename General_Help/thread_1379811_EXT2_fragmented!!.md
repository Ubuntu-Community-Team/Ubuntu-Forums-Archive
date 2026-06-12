---
title: "EXT2 fragmented!!??"
date: 2010-01-13
forum: General Help
---

### Post by lingdao67 on 2010-01-13
Hi all,
 
Some MAC consultant has persuaded my client that the Linux server needs to be defragmented! I know that the general consensus that it is unnecessary, but in this case he could be correct since the ext2 (or 3) disk is 92% full. 
 
What are the steps to performing this this operation it it is indeed necessary?
 
Thanks,
 
l

---

### Post by ramjet_1953 on 2010-01-13
It sounds like the consultant is trying to get a bit more money!

However, as the disk is 92% full, cleaning out un-needed files would be a good idea.

If this is not possible, it sounds like a larger drive may be in order.

Regards,
Roger:)

---

### Post by john newbuntu on 2010-01-13
The e2fsck command has a "-E fragcheck" option that might give you an idea on how fragmented the disk is.  But in general, the more closer you get to the max size, the more fragmented your drive is.  I agree with Ramjet's suggestions although I am not sure on the $$ part.

You could try the good old tar command to see if defragging goes down or use a script like pyfragtools for defragging.

---

### Post by running_rabbit07 on 2010-01-13
I agree that either a purging of unused files or a hard disk upgrade is in order. As far as checking fragmentation or defragging goes, I have no idea how to do it with Linux.

---

### Post by MaxIBoy on 2010-01-13
"fsck -E fragcheck" tried to actually run a filesystem check and repair on my mounted filesystem! I'd recommend booting from a liveCD and unmounting everything before you run that. Lucky for me it only cleared two inodes and those were probably just my browser cache (only thing open at the moment.)

---

### Post by lingdao67 on 2010-01-13
Here's a little more clarification and another question.  The disk itself is only used to store data, I have an entirely separate drive for the system.  Do I still need to unmount the disk?

---

### Post by fancypiper on 2010-01-13
Always unmount a partition to fsck it. fsck should warn you if it is mounted.

---

### Post by Ugluk on 2010-01-13
The simplest way to defrag your drive is to boot from live CD, copy the entire filesystem to other disk, format the disk and restore files; defragmenters are not effective when disk is nearly full.

---

### Post by lingdao67 on 2010-01-13
Today I was at the client site mentioned earlier and the MAC consultant had actually tried to defrag one of the MAC's yesterday. After running the defrag over night, the unit froze up and now cannot boot!
:wink:
 
It looks like we may just get a larger disk.

---

### Post by lingdao67 on 2010-01-15
One more thing, the nearly full disk is 6 % fragmented according to fsck.  And the files system is ext3.

---

### Post by nexoncore on 2010-01-15
6% Fragmentation is nothing serious, I had a similar issue and it was meerly a case that the hard drive was pritty much coming to the end of its life span. As advised above, you would be best of backing up the data, formatting the drives fully ( would advise formating to ext 4 at the same time ) then restoring your data.

Also, it is advised to remove old, unused data. When I was a web developer and had this issue, I kept frequent backups of data. When the system I was on was getting full, I just backed up older, unused data or archive data onto DVD's and stored in a filing cabinet in the same room as the server.

---

