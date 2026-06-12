---
title: "about Inodes and Directories"
date: 2010-11-14
forum: General Help
---

### Post by Konbuntu on 2010-11-14
im trying to follow a tutorial but there's this one par that's making me scratch my head for a while now:

"open a directory on the device that you want to monitor and use ls -i command to display a list of all file names and their inodes number..." 

what shoul i do... i'm currently reading "understanding file systems"

hopefully someone will help me


thanks in advance

---

### Post by matt_symes on 2010-11-14
Hi,

From this thread

[http://ubuntuforums.org/showthread.php?t=432112](http://ubuntuforums.org/showthread.php?t=432112)

When a file system is created, data structures that contain information  about files are created. Each file has an inode and is identified by an  inode number (often "i-number") in the file system where it resides.  Inodes store information on files such as user and group ownership,  access mode (read, write, execute permissions) and type of file. There  is a fixed number of inodes, which indicates the maximum number of files  each filesystem can hold.

A file's inode number can be found using the ls -i command, while the ls -l command will retrieve inode information.

You can also find inode using the linux stat command, and if youve come  from a windows background, you can think of inodes as similar to the  file allocation tables in windows.

Also this might interest you.

[http://en.wikipedia.org/wiki/Inode_pointer_structure](http://en.wikipedia.org/wiki/Inode_pointer_structure)

Kind regards

---

