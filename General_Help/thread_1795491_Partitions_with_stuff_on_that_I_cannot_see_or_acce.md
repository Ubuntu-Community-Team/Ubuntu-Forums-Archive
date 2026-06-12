---
title: "Partitions with stuff on that I cannot see or access"
date: 2011-07-02
forum: General Help
---

### Post by mrchumpley on 2011-07-02
After great success solving a two year old problem here I thought I'd try the other big problem I have....

After a problem updating from 8.04 to 10.04 I re-formatted and partitioned one of my two hard drives. The second drive remain unchanged.

I have managed to give myself permission to read, write and execute in the partitions on the second drive (sdb1, sdb2 and sdb3) yet the files that I put there before the upgrade cannot be 'seen'. When I open each partition all I can see is a 'Lost and Found' folder which is empty. The partition appears empty when exploring /media yet when I right-click and look at 'Properties' it says that 5.6GB of the 90GB is used! 

How can I access these files on the partition?

Many thanks (in anticipation!)

Nevil

---

### Post by Morbius1 on 2011-07-02
From your other post /media/Documents should be one of the mount points on the second drive. What is the output of the following command:
```
ls -al /media/Documents
```If there's a whole mess of files just the top 10 or so will do. But we also need the very first two lines - the lines ending in "." and ".."

---

### Post by mrchumpley on 2011-07-03
Hi Moribus and thanks for helping me again! 

Apologies for the delay in responding - I went to bed.

Here is what I get for each partition:

nevil@Ubuntu1:~$ ls -al /media/Photos
total 28
drwxr-xr-x 4 nevil nevil  4096 2011-07-02 22:42 .
drwxr-xr-x 9 root  root   4096 2011-07-03 07:43 ..
drwxr-xr-x 2 nevil nevil 16384 2008-07-28 10:53 lost+found
drwxr-xr-x 2 nevil nevil  4096 2011-07-02 22:42 new
nevil@Ubuntu1:~$ ls -al /media/Video
total 32
drwxr-xr-x  5 nevil nevil  4096 2011-06-24 22:34 .
drwxr-xr-x  9 root  root   4096 2011-07-03 07:43 ..
drwx------ 47 nevil nevil  4096 2011-06-24 22:34 ARCHIVEMUSICFLAC
drwxr-xr-x  3 nevil nevil  4096 2011-05-27 22:17 Germany trip 2011
drwxr-xr-x  2 nevil nevil 16384 2008-07-28 10:53 lost+found
nevil@Ubuntu1:~$ ls -al /media/Documents
total 24
drwxr-xr-x 3 nevil nevil  4096 2008-07-28 10:53 .
drwxr-xr-x 9 root  root   4096 2011-07-03 07:43 ..
drwxr-xr-x 2 nevil nevil 16384 2008-07-28 10:53 lost+found


What does it mean? 

Just to re-iterate, the Documents partition is empty when I look in with File Browser but Properties shows 5.1GB of 96.9GB used. Properties also tells me it's a folder (inode/directory) with contents 1 folder (16KB). File system type is ext3/ext4.

Thanks again.
Nevil

---

### Post by dino99 on 2011-07-03
can you check these folders after booting on livecd ?

---

### Post by mrchumpley on 2011-07-03
Using LiveCD I have the same problem. No change.

---

### Post by Morbius1 on 2011-07-03
I'm afraid I have no answer for this one. If "ls -al" shows no content then I'm fairly certain there is no content. The 5.6GB is a mystery. Is there any chance you formatted the partition that holds /media/Documents in error?

---

### Post by mrchumpley on 2011-07-05
It is possible that I re-formatted the partitions. 

Would you suggest that the best solution would be to save any visible data and re-format the partitions?

Cheers
n

---

