---
title: "Find non-duplicate files"
date: 2010-08-13
forum: General Help
---

### Post by phaed on 2010-08-13
I have an internal hard drive and an external hard drive, both with about 350 GB of data.  The data came from the same source, but over the last couple of years, different people have moved files around to different directories, and some files have been deleted.  Now I want to merge all the files onto the internal hard drive.  I estimate that 80% of the files on the external hard drive are the same, so I don't want to copy 290+ GB of data over when I already have it.

Therefore, I need a way to find just the files on the external hard drive that don't already exist on the internal one.  In other words, I need to create two lists of file names irrespective of directories and compare them, selecting only the file names that exist in one list OR the other.

I've Googled for solutions but can't find anything suitable.  There are ways to create text files of the file names and compare them with diff, but they have to be in the same order, and since these files are in vastly different directories, that won't work.

---

### Post by warddr on 2010-08-13
If you've got some programming skills you can make a database with 2 tables.
1 table with the files that are on the internal harddrive, and one table with the files on the external harddrive.
You can also add a column with a md5 hash if you want to be shure the file is an exact duplicate, but it will take some time to compare. A less accurate, but faster way to check is to add the exact document size in bytes in a column.

If you've got the database you can compare them, and generate a list of files that have to be copied.

---

### Post by phaed on 2010-08-13
Nevermind, this turned out to a lot simpler than I thought.  I was trying to do

ls -R /path/to/dir1 > results1.txt
ls -R /path/to/dir2 > results2.txt
diff results1.txt results2.txt

In that case, diff goes line by line, but you can run it directly on directories:

diff -r /path/to/dir1 /path/to/dir2

And it looks for the same files names irrespective of the directory they are in.

That's exactly what I needed.

---

### Post by DaithiF on 2010-08-13
Hi,
you could do something like:
1. get a listing of filename-filesize filepath for each drive, sorted by filename-filesize
2. do a diff of the first column from each file to see whats in drive1 thats not in drive2
3. and grep these filename-filesizes from the drive2contents to pick out the full paths that you'll then need to copy across to drive1

or: 
```
find drive1 -type f -print0 | du -b --files0-from=- | sed -r 's#^(.*)\t(.*)/([^/]+)$#\3-\1\t\2/\3#' | sort > drive1contents

find drive2 -type f -print0 | du -b --files0-from=- | sed -r 's#^(.*)\t(.*)/([^/]+)$#\3-\1\t\2/\3#' | sort > drive2contents

diff <(cut -f 1 drive1contents) <(cut -f1 drive2contents) | grep "^>" | cut -c3- | grep --file=- drive2contents | cut -f 2

```the output from the last command should be the paths to the files on drive2 that you'll need to copy to drive1 to make drive1 the superset of both.

---

### Post by phaed on 2010-08-13
Thanks Daith!  That worked even better because it cut out the directory names.

---

### Post by phaed on 2010-08-13
deleted

---

