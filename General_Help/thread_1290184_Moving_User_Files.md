---
title: "Moving User Files"
date: 2009-10-13
forum: General Help
---

### Post by M70JRD on 2009-10-13
I'm looking for help, to which I'm sure there must be a simple solution.
I have a network at home consisting of a sever which uses NIS and NFS for managing logins and file transfers.
Server one, which has user accounts in /home/users/user1 is to be replaced, so i have built the new one and created user accounts, I need to copy all the data from the user area from the old server to the new.
How do I do this whilst preserving all the user info? So far I have mounted the area on the new server and used cp -p to copy the files over. All the files transfer but when I use firefox, it states its already in use.
Thanks in advance

John

---

### Post by upbeat.linux on 2009-10-14
Navigate to your user profile then mozilla (or firefox) profile within.  Delete the lock file.

[http://kb.mozillazine.org/Profile_in_use]("http://kb.mozillazine.org/Profile_in_use")

---

