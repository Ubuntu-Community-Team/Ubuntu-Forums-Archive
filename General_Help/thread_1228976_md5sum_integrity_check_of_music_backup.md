---
title: "md5sum integrity check of music backup"
date: 2009-08-01
forum: General Help
---

### Post by IcarusR on 2009-08-01
Hi all
I have 350 Gb of flac music files on a mirrored array on my server. 
I have purchased two larger drives to replace the current ones.
I have two backups of the collection.

Before I restore a backup to the new drives I need to check & confirm their integrity.
I have used md5sum to create a text file with md5sums of the original collection.
```
 md5sum /music/*/*/*.* > md5sum.txt
```
I need md5sum to use this text file to check the sums it calculates of my backup.
ie compare md5sum values of backup with those in the text file, thus enabling me to asses the integrity of my backup.
The problem is that the path to my backup is different, obviously, to my music collection.
The collection path is written to the text file & read when checking, so it checks the music collection not the backup.

Can someone help me out here please ?
Any ideas how to check the integrity of my backups ???

Cheers

---

### Post by Brandon Williams on 2009-08-02
Dealing with changes to the full path of the file should be easy enough. For example:
```
while read CKSUM FILE; do
    BKUP_FILE=$BKUP_PATH/${FILE#/music/}
    echo $FILE $BKUP_FILE
done << md5sum.txt
```
This loop shows how to extract the md5sum and the file name from each line and construct the name of the backup file by stripping the base path "/music/" from the filename in md5sum.txt and replacing it with the base path of where the backup files are stored.

---

### Post by IcarusR on 2009-08-04
Brandon

Thanks for your reply, will give it a go.
I had found a less elegant solution... run md5sum from within the backup directory @ a point where the paths are the same.

Thanks again.

---

