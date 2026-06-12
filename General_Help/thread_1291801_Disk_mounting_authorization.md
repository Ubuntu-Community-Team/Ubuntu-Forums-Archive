---
title: "Disk mounting authorization"
date: 2009-10-15
forum: General Help
---

### Post by Ugluk on 2009-10-15
Each time when I'm trying to open my NTFS hard drive, I'm getting Authorization prompt, issued by "org.freedesktop.devicekit.disks.filesystem-mount-system-internal". When I check "Authorizations" applet, I see that whole org.freedesktop.devicekit.* tree is missing from there. How can I prevent it from happening?

---

### Post by Ugluk on 2009-10-18
Anyone?!

---

### Post by tz1 on 2009-11-04
I would also like to know.

The entry is in /usr/share/polkit a few levels deep, but it is just a bunch of XML junk which I don't think anyone has documented anywhere.

You mention an authorization applet, but I can't find that.  What is it called or how is it accessed?

---

### Post by tz1 on 2009-11-04
correction - 

Directory is:

/usr/share/polkit-1/actions

The

org.freedesktop.devicekit.disks.policy

 file contains the action ID which indicates authorization is required.

---

### Post by tz1 on 2009-11-04
Edit the sections for filesystem-mount-*  so that the defaults / allow_* read "yes" instead of no or auth_* (the action id=xxx is given in the details in the auth popup).

---

