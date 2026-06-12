---
title: "system hanging when swapping user"
date: 2011-10-27
forum: General Help
---

### Post by rirkobson on 2011-10-27
I have two users set up and both are usually logged in. the system was installed with 11.4 and was working with no problems swapping between the two users. since upgrading to 11.10 the system hangs with a black screen when swapping user after both have been logded in. if only one user has been logged in and the second is logged in this works normally.

---

### Post by mjuhasz on 2011-10-27
There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/829221") in the samba package that makes lightdm hang.

It has been fixed in the samba version [2:3.5.11~dfsg-1ubuntu2.1]("https://launchpad.net/ubuntu/oneiric/+source/samba/2:3.5.11~dfsg-1ubuntu2.1") which is already in the proposed repository. Soon it will make it into updates.
If you want to test it you can [enable the proposed repository]("https://wiki.ubuntu.com/Testing/EnableProposed") and update samba.

---

