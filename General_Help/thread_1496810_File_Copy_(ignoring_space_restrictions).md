---
title: "File Copy (ignoring space restrictions)"
date: 2010-05-29
forum: General Help
---

### Post by seawolf167 on 2010-05-29
Is there a way to copy files from one hard disk to another but ignoring space restrictions (and skipping identical files)? 

I have 2 identical 1TB disks;
Disk 1 - full (only ~20 GB free space)
Disk 2 - ~3/4 full (this disk contains an earlier copy of the Disk 1 items; i.e. all of the items on this disk are on Disk 1, they are not compressed or anything, they were just dragged-and-copied over from Disk 1 probably about 6 months ago)

What I want to do is copy Disk 1 over to Disk 2, but when I try to do that I get a message saying something along the lines of "ERROR: XXX amount of disk space available YYY amount needed" and I am unable to continue.

I would very much rather not have to delete the items from Disk 2 and start the copy over from the very beginning as it would probably take an entire day (and need babysitting incase anything happened).

In Windows I used a program called "TeraCopy". I would drag the items from Disk 1 to Disk 2 and it would give me a prompt allowing me to ignore the fact that there isn't enough free disk space available. This, however, wasn't a problem because essentially in the very next prompt I was given an option to skip or overwrite all files that were the same (I choose to skip all identical files, thereby making the file transfer only ~1/8 of the disk [just the new items]).

I am using
Ubuntu 9.10 2.6.31-21-generic x86_64
Both disks are formatted NTFS (Disk 1 is internal, Disk 2 is currently connected via eSATA)

Any thoughts/ideas would be appreciated!

EDIT: This disk does not contain any OS files (Windows, Ubuntu or otherwise), it is mainly rendered images & videos

---

### Post by seawolf167 on 2010-05-29
So I might have just solved my own problem with this:

```
 cp -r -u -v disk1 disk2 
```

it is my understanding that this will copy from disk1 to disk2 recursively only transferring new or missing files and shows the output in the terminal.

I love the command line! (once I figure out all the options & names for the programs that is...)

---

### Post by J V on 2010-05-29
Yes that works (the v isn't neccesary, and you can add the options together)```
cp -ru disk1 disk2
```
Also, look into rsync, it will only copy the changes over (So if you make a small change to a large file it will only copy the small change, rather than the entire large file)

You can also work with svn to make it "Remember" all the previous versions just by using the differences between the files (a years worth of changes tends to be only twice the size of the original file)

---

### Post by CharlesA on 2010-05-29
rsync would work well. :-)

---

### Post by seawolf167 on 2010-05-29
Awesome, thanks for the replies, I'll test them out :)

---

