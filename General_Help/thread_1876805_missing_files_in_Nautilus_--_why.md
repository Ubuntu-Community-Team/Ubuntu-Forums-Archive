---
title: "missing files in Nautilus -- why"
date: 2011-11-06
forum: General Help
---

### Post by motomixon on 2011-11-06
I downloaded some tar.bz2 files from the MySQL site to a specific directory, but when I went to unpack them, they were not appearing!?

Here is a directory listing:
============begin=======
masonmd@blacktower:~/mysql_employee$ ls -g
total 52244
drwxr-xr-x 2 masonmd     4096 2011-11-06 09:12 employees_db
-rw-r----- 1 masonmd     6511 2009-03-29 17:44 employees_db-code-1.0.6.tar.bz2
-rw-r----- 1 masonmd 26706427 2009-03-29 18:05 employees_db-dump-files-1.0.5.tar_001.bz2
-rw-r----- 1 masonmd 26706427 2009-03-29 18:05 employees_db-dump-files-1.0.5.tar.bz2
========end=========
The weird part, the first bz2 file shows in nautilus, but the two db-dump files do not. 
I cannot figure why this is happening  :confused:, but would like to learn why so I don't get caught by this one again!!  :(

TIA

Ubuntu 11.04

---

### Post by dcstar on 2011-11-07
> **motomixon said:**
> I downloaded some tar.bz2 files from the MySQL site to a specific directory, but when I went to unpack them, they were not appearing!?

Here is a directory listing:
============begin=======
masonmd@blacktower:~/mysql_employee$ ls -g
total 52244
drwxr-xr-x 2 masonmd     4096 2011-11-06 09:12 employees_db
-rw-r----- 1 masonmd     6511 2009-03-29 17:44 employees_db-code-1.0.6.tar.bz2
-rw-r----- 1 masonmd 26706427 2009-03-29 18:05 employees_db-dump-files-1.0.5.tar_001.bz2
-rw-r----- 1 masonmd 26706427 2009-03-29 18:05 employees_db-dump-files-1.0.5.tar.bz2
========end=========
The weird part, the first bz2 file shows in nautilus, but the two db-dump files do not. 
I cannot figure why this is happening  :confused:, but would like to learn why so I don't get caught by this one again!!  :(

TIA

Ubuntu 11.04

Possibly because of the file size and Nautilus is still scanning through them looking for icons or doing indexing before you give up? (only a guess).

See if your hard disk is busy when you use Nautilus.

---

### Post by -kg- on 2011-11-07
Another thought....

Are the dump files hidden?  Try viewing the folder and pressing Ctrl-H.  See if you can see them then.

---

### Post by motomixon on 2011-11-09
Hey All,
Thanks for the input.

Well.....,
the one downloaded/extracted file showed up, so I am assuming that Nautilus is current/updated in what it displays.

And yes,  I used the Ctrl + H to display hidden files, so that didn't fix it. 


Oh well, Murphy's law still rules....

Thanks,

---

