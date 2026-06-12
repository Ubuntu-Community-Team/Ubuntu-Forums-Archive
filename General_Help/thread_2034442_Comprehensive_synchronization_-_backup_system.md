---
title: "Comprehensive synchronization - backup system"
date: 2012-07-28
forum: General Help
---

### Post by CanisMajorWuff on 2012-07-28
Does somebody know a synchronization system with file version control?

I have about 3-5 GB of data which I want to synchronize with another storage (directory). Both directory should store the last versions of files. So if any changes occur in one directory, they must be reflected into another one and vice verse. Also all changes ( not matter how large they were: remove of 1GB file or a simple text line addition) should be stored. Of course, rollback should be available.

To make a certain notion of what I am talking about here it is some examples.

1. Dropbox - system make a synchronization of local storage and remote. It has a backup and version control feature. Very good system I like it, I use it, but it only works for local directory and for remote Dropbox storage. However I need to use it for local data and more flexible job configuration.

2. VSC (mercurial, git, svn, ....) - synchronization of repositories of text files. Very comprehensive systems, I use them for my documents, there were no occurrences when I could not find something in their capabilities ever. But how I have said it is only for text files.

---

### Post by drmrgd on 2012-07-28
It sounds like you may be looking for something like rsnapshot ([http://rsnapshot.org/](http://rsnapshot.org/)).  You can make snapshots of files as frequently as hourly (I believe), and you can store multiple iterations of each (so for example, you can have 24 backups for a full day if you do it hourly).  I don't think you can sync in real time with the utility like you would with Dropbox, though.  So, that could be a deal breaker.

Have a look, though to see if it fits your needs at all.  I use it,and it runs great and is very easy to set up.

---

### Post by CanisMajorWuff on 2012-07-29
No, it is not what I am looking for. I don't need a scheduled backup of entire directory. I need a system which store (make a backup) of old file versions or deleted files. I am looking for something like Dropbox but for local storages.

---

