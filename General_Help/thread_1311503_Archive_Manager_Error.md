---
title: "Archive Manager Error"
date: 2009-11-02
forum: General Help
---

### Post by n4lbl on 2009-11-02
First, I did a search using the three words in the subject to no avail.

I've become reliant on Ubuntu and it is time to start protecting myself with backups.  Using the Archive Manager I tried to backup my user files.  The error text is "An error occurred while adding files to the archive.  Command exited abnormally"  If I try to use the archive it says 
"An error occurred while loading the archive.  Command line output  
        gzip: stdin: unexpected end of file
        tar: Unexpected EOF in archive
        tar: Error is not recoverable: exiting now"

I'm running an up-to-date 9.04 and writing to a USB external disk with a fat32 file system.  The failure is at 4 GB if that is pertinent.

I had partitioned the disk with an ext3 file system but had (I think) ownership problems (owned by root) and went back to fat32 just to get this done.

thanx,,,

---

### Post by liquidbee on 2009-11-02
FAT32 max file size is *4Gb - 1 byte* ( you are stepping over it ).

---

### Post by n4lbl on 2009-11-02
Nuts!!  I was afraid of something like that.  Thanks.

I'll partition an area and struggle with that.

Thanks again.  BTW, how do I mark this as solved??

---

### Post by liquidbee on 2009-11-02
> **n4lbl said:**
> Nuts!!  I was afraid of something like that.  Thanks.

I'll partition an area and struggle with that.

Thanks again.  BTW, how do I mark this as solved??

Thread tools ( top right from your first post ) - Mark as solved

---

