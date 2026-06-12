---
title: "How to specify network path filespec in a command line?"
date: 2010-08-24
forum: General Help
---

### Post by VanillaMozilla on 2010-08-24
I need to add a network path to a configuration file, but I can't figure out how to write the path.

The command
dir \\computername\sharename
works in a Windows command line.

ls //computername/sharename/
does not work under Linux.  ("No such file or directory.")
ls smb://computername/sharename/ does not work either.

Nautilus shows the location as smb://computername/sharename/, and I can read and write in the shared directory, so it's mounted and I have access.

So how do I get it to work?  How do I specify the path so a command line will recognize it?

---

### Post by VanillaMozilla on 2010-08-25
Bump.  These go out of sight fast.

---

### Post by VanillaMozilla on 2010-08-27
OK, I got it.  This wasn't easy!

1. Installed smbfs

2. sudo mkdir /mnt/somename

3. Added
//computername/sharename /mnt/somename cifs guest,uid=1000,iocharset=utf8,codepage=cp850  0  0

to /etc/fstab.  Now you can access it as /mnt/somename.


Optional:
1. If you want it to appear on the desktop, mount it in /media/somename instead.

2. If desired, add it as a bookmark to the Places menu.

---

### Post by VanillaMozilla on 2010-09-01
Not solved after all, and I don't have any idea what's wrong.

/mnt/somename
is empty, when viewed either from Nautilus or the command line.


I don't know why I thought it was solved.  It may have been solved, but a later configuration change broke it; or I may have been viewing local files in the /mnt directory by mistaken.

---

