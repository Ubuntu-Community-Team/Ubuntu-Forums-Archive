---
title: "smbmount (cifs) question"
date: 2010-08-05
forum: General Help
---

### Post by Apnu on 2010-08-05
Hello all,

This is on a Lucid Lynx system.

I'm trying to use smbmount (cifs) to mount a remote file system to a directory in my home.

When I execute: smbmount //SERVER/FOLDER /home/USERNAME/backup -o username=USERNAME,password=PASSWORD,rw

I get the following error: 
  > mount error(1): Operation not permitted
  Refer to the mount.cifs(8 ) manual page (e.g. man mount.cifs)

I read the man page and don't see that I'm doing anything wrong.

But if I sudo to root and try:  
smbmount //SERVER/FOLDER /home/USERNAME/backup -o username=USERNAME,password=PASSWORD,rw

It works as expected.  I thought maybe I didn't have permission to use smbmount or mount.smbfs but I do. This same command worked fine on Hardy, Intrepid, and Karmic.  So what's going on here?

---

### Post by Apnu on 2010-08-05
SOLVED.  

Had to enable the sticky bit (sudo chmod +s) to /sbin/mount.cifs /sbin/mount.smbfs and /sbin/umount.cifs

---

