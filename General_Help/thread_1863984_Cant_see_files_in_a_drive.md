---
title: "Cant see files in a drive"
date: 2011-10-18
forum: General Help
---

### Post by shashanksingh on 2011-10-18
I have an ntfs partition named Jupiter. I cant see its contents.

After mounting it to /media/Jupiter from places, nautilus shows its empty, but right click-> properties shows that the data is there.

An ls gives me this

ls: reading directory /media/Jupiter: Input/output error


Accessing it is no problem from Windows7, so atleast the data is there

---

### Post by 2F4U on 2011-10-18
May be a dumb question but do you have read permission?

---

### Post by Mark Phelps on 2011-10-18
Since you can access the partition from Win7, I would run a CHKDSK on it from inside Win7.

---

### Post by collisionystm on 2011-10-18
> **Mark Phelps said:**
> Since you can access the partition from Win7, I would run a CHKDSK on it from inside Win7.

+1

Be careful with handling NTFS partitions in Linux. NTFS support is not perfect!

---

### Post by shashanksingh on 2011-10-19
Ok now I do remember something.

The last time I accessed it from windows, I got many random numbered folders starting with 'orbit' which were all empty and I couldn't figure out what they were doing there. I did not intentionally install anything like the orbit downloader.

Now that I did the chkdisk, the disk is visible again but with all those folders back. I have attatched a screenshot.

Also, there was is an 'aptdaemon' named folder, which I have no idea about its sudden occurence.

---

