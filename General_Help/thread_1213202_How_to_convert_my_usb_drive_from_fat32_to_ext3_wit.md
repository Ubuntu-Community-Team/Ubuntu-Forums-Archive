---
title: "How to convert my usb drive from fat32 to ext3 without formating"
date: 2009-07-14
forum: General Help
---

### Post by JuanC on 2009-07-14
Hi to all,

I am transforming all my data to linux formats but i have a problem.

I have an usb drive in fat32 that i want to transform to ext3, but all tools I find need to format this drive to convert to ext3, that isn't a good option, my usb drive have a lot of data I don't want to lost.

How to convert my usb drive from fat32 to ext3 without formating?
 
If this doesn't exist, i think ubuntu developers team should make a tool to this, because it helps in the proccess to Linux migration.

---

### Post by itsjareds on 2009-07-14
If you have filled the drive less than halfway, you can create another partition on the drive and copy your files there, then format where your files were and then copy the files back.

---

### Post by Blacklightbulb on 2009-07-14
OK first off if you have to change for fat32 to ext3 you must format in a way or another.

Easy Steps:
1. Partition you Usb drive in 2; I filled with data and on with the extra free space.
2. Format the extra free space to ext3
3. Fill the newly formated partition with some of your data form the other partition.
4. Create a partition with the free space and format to ext3 and so on until you have many ext3 partitions
5. Then merge the partions.

Or you can just backup data to pc, format to ext3 and put back.:lolflag:

---

### Post by RD1 on 2009-07-14
Here's a tip. 

If you have that much data that you don't want to loose, you need a backup anyway!

Purchase another drive. Create a EXT3 partition on it. Copy your data to the new drive. Format the old drive EXT3. Copy the data back.

Now your old drive is EXT3 and you have a backup.

Have a nice day. :)

---

### Post by zetman on 2009-07-14
> **JuanC said:**
> Hi to all,

I am transforming all my data to linux formats but i have a problem.

I have an usb drive in fat32 that i want to transform to ext3, but all tools I find need to format this drive to convert to ext3, that isn't a good option, my usb drive have a lot of data I don't want to lost.

How to convert my usb drive from fat32 to ext3 without formating?
 
If this doesn't exist, i think ubuntu developers team should make a tool to this, because it helps in the proccess to Linux migration.

fat32 and ext3 are two different formats for storing files.  Changing from one format to another is, by definition, reformatting.

Lets say you had a collection of, oh say DVDs and that you kept them sorted by title.  Then later you decided that you wanted to keep them sorted by genre.  Now the DVDs are like your files and the method of sorting is like your file system.  What you're asking is like asking if there is a way to resort the DVDs without having to move any of them.

Blacklightbulb's last suggestion is likely the best case: backup, reformat, restore.

---

