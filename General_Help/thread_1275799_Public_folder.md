---
title: "Public folder"
date: 2009-09-26
forum: General Help
---

### Post by Worp8d on 2009-09-26
Hi,

I am using Ubuntu 9.04.  I want to set up two user accounts - one admin and one for everyone else who uses this public computer.  I want a directory - /home/public - that all of the common files go into.  I want both users to be able to access all files and to read and write all files.  I can set the permissions for this easily enough once the files are created.

The problem is that every time a file is created I have to re-set the permissions so that both users can access, which I can do for either that file or the whole tree, but I don't want to have to do that.  Is there any way I can set up the directory so that ANY file/directory that is created in this folder is automatically set to have the correct permissions?

---

### Post by Worp8d on 2009-09-26
I gave in too early.  The solution was to modify the extended ACLs (Access Control List) for the directory and apply the "d" (default) option so that all of the permissions are automatically assigned to files created in the directory.  [Here]("http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists") is the article I followed, it worked like a charm.  :)

---

