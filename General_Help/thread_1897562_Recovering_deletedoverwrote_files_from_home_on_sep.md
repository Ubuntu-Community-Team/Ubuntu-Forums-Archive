---
title: "Recovering deleted/overwrote files from home on separate partition, ext4, &amp; encrypted"
date: 2011-12-19
forum: General Help
---

### Post by jsmtrd on 2011-12-19
Recovering deleted/overwrote files from home on separate partition, ext4, & encrypted


The version of ubuntu I am running is about a year old.

 

 I was trying to set up a script (ironically a backup script, but for something else) and overwrote about 40 gb of stuff in my /home/[username]/Documents directory in my ext4 encrypted home partition. I think I must have replaced Documents with another folder called Documents that has a few mb of data in it. At least that is what I see now when I look at it. Since it is encrypted normal recovery tools do not seem to be able to read the files.
 

 I looked at /home/.encrypfs/[username]/.Private and it is still has over 55 gb of data in it so I think the data must still be in there someplace. I have a copy of the home partition, so I can mount it as read only and then mount the encrypted files/partition (whatever it is) and read them. I ran extundelete on the home partition and the home partition with the encrypted files/partition mounted. It found only a few files each time, none of what I was looking for. I then ran scalpel on the partition but it does not find much of anything. I more or less expected that since the files are encrypted and therefore will not look like any files it knows about.
 

 Question One: Is there anyway to make scalpel or some other program recognize the encrypted files as a file type? So that I can scan and recover them then unencrypt them latter.
 

 Question Two: Is there some way to do a raw copy of the encrypted data with dd or something like that through ecryptfs like when mounting (i.e. mount -t ecryptfs … ). Then we would have some devise full of this raw unencrypted data to scan.
 

 Question Three: Is there a devise (i.e. /dev/[whaterver]) that accesses the raw unencrypted data after it has been mounted like as if it was a partition? So I could point scalpel or some other tool to that and have it scan it for files just like a physical partition.
 

 Thanks in advance for your help.

---

### Post by jerrrys on 2011-12-21
I do not use encryption, but two ideas:

[Test Disk]("http://www.cgsecurity.org/wiki/TestDisk") && [Clonezilla]("http://clonezilla.org/")

---

