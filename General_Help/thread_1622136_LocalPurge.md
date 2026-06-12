---
title: "LocalPurge?"
date: 2010-11-15
forum: General Help
---

### Post by Quarkrad on 2010-11-15
(10.10)  Now and again I get this message in terminal after installing - 

You have to configure "localepurge" with the command

	      dpkg-reconfigure localepurge

	  to make /usr/sbin/localepurge actually start to function.

	  Nothing to be done, exiting ...

If I enter the command dpkg-reconfigure localpurge as asked I get:

root@dadubuntu:/home/dad# dpkg-reconfigure localpurge
Package `localpurge' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: localpurge is not installed.

When I type localpurge in Synaptic there is no entry.  Any help appreciated -newbie

---

### Post by lotharmat on 2010-11-15
it is called local_e_purge

---

### Post by Quarkrad on 2010-11-15
Yes - you were right!  The command now works!  Thanks.

---

### Post by lotharmat on 2010-11-15
Glad it is working!

---

