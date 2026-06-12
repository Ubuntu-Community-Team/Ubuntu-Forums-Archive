---
title: "low disk space on copy of large files"
date: 2010-08-31
forum: General Help
---

### Post by dreaminhere on 2010-08-31
I have a 32 gig sdd for my / that is only 6.5 gig full.  I have 2 1T disks that I store my data on.  One of the files on those data disks is a virtual box image that is 28 gig.  When I try to copy that file to anywhere (including external drive), I get a file input/output error at around 25.5 gigs. 6.5 + 25.5 = 32 gig  The issue is that when it copies the file, it does something with my sdd drive so that it thinks it is full, even though I am not copying the file to that drive.  I've confirmed this by running df -h before, during, and after copy.  What can I do to enable this file to copy?

---

### Post by dreaminhere on 2010-09-05
bump

---

### Post by JBAlaska on 2010-09-05
How about you tar or rar it and span it to bite sized volumes.

```
rar a -v700M <archive_name> <file/directory_to_archive>
```

---

### Post by dreaminhere on 2010-09-05
JB

Thanks, that's a good workaround for backups, but I still have other problems related to this same issue.  For instance, I can't clone a virtual machine because it ends up as disk full.  Is there a way to tell it to use the free space on a different disk?

---

### Post by dreaminhere on 2010-09-05
It looks like certain things use a temp directory in root and then transfer them over to the location they should be.  What is that temp directory and can I map it to a different location?

---

### Post by dcstar on 2010-09-06
> **dreaminhere said:**
> It looks like certain things use a temp directory in root and then transfer them over to the location they should be.  What is that temp directory and can I map it to a different location?

/tmp and you can have it mounted to another partition on a different drive. Here is my fstab with my /tmp moved off my SSD:

```
#/dev/sdb7
UUID=59648818-b89b-4a5c-bc8b-1f36f81ddbe6 /tmp ext2 defaults,noatime 0  0 
#
```

Be aware the /tmp has special permissions that **must** be set for it to work - or your system may not even boot up! Do a forum/Google search for detailed instructions on this.

---

### Post by dreaminhere on 2010-09-06
Looks like I had two different problems.  One was when I tried to clone a virtual disk and used relative paths.  This gave me a disk full error message because of limited space on my ssd.  Using full paths took care of this problem.  The other problem was a bad sector on my hard drive which created problems in copying the large file.  Archiving the file and then extracting allowed a copy to be made of that file and then I just deleted the original. I assumed that the issues were related to eachother but they really weren't. Thanks for everyones help.

---

