---
title: "Google Desktop Won't Recurse Subdirectories"
date: 2010-02-15
forum: General Help
---

### Post by raywood on 2010-02-15
I'm using 64-bit Ubuntu 9.10.  I have installed the appropriate version of Google Desktop for Linux (GD).  I want GD to index the subfolders under /media.  Those subfolders include several data partitions containing files that I want GD to search.

In GD, I've changed the settings to include /media as a folder to index.  This results in a small number of files being indexed.  It seems that GD is indexing only /media itself, and not the subfolders under /media.

I have tried adding * (i.e., /media/*) to the folders list in GD.  This does not seem to work.  How can I get GD to index /media/* ?

---

### Post by tom4everitt on 2010-02-15
Perhaps its not indexing because you do not own the directories in /media or do not have sufficient permissions. 

What is the output of 

ls -ld /media

and

ls -l /media


(and what is the name of your user).

---

### Post by raywood on 2010-02-15
drwxr-xr-x 12 root root 4096 2010-02-15 10:22 /media

drwxrwxrwx  1 root root  4096 2010-02-13 10:48 BACKROOM
lrwxrwxrwx  1 root root     6 2010-01-18 13:33 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2010-01-18 13:33 cdrom0
drwxr-xr-x  2 root root  4096 2010-01-18 13:33 cdrom1
drwxrwxrwx  1 root root  4096 2010-02-04 08:30 COLDSTORAGE
drwxrwxrwx  1 root root 28672 2010-02-12 23:05 CURRBACKUP
drwxrwxr-x 12 ray  ray   4096 2010-02-13 20:30 CURRENT
lrwxrwxrwx  1 root root     7 2010-01-18 13:33 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2010-01-18 13:33 floppy0
drwxr--r--  2 root root  4096 2010-01-18 17:44 PROGRAMS
drwxr-xr-x  2 root root  4096 2010-01-29 21:57 UBU-START
drwxrwxr-x 11 ray  ray   4096 2010-01-22 08:58 VMS

My username is ray.

I'm sure you're right -- I keep forgetting this is not WinXP.  But how can I rectify it?

---

### Post by tom4everitt on 2010-02-16
From the output you can tell the following:

-most of the folders are owned by root, not by ray.
-none of the folders lack reading permissions (for anyone).

(here's a link on how to read that output: [http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/))

since there is no lack of reading permissions I actually doubt this is the error. Especially since it doesn't not even index the folders owned by you (or does it?). 

If you want to experiment with owners and permissions the following commands are what you need: 

chown username:groupname nameoffile (changes the owner of a file/folder).
chmod XXX nameoffile (changes the permissions for a file/folder).

run as sudo if necessary, add a -R flag if you want the change to take effect on subfolders etc. See the link for more details.

---

