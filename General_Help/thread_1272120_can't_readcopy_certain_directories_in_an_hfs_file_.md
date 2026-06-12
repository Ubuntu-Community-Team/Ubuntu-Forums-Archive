---
title: "can't read/copy certain directories in an hfs file system"
date: 2009-09-21
forum: General Help
---

### Post by BattlePanic on 2009-09-21
Yesterday, a friend of mine came by to drop off some files last night and he brought with him an an external usb hard drive with an hfs partition (he's a mac user).

When I plugged it in, the drive was mounted automatically under Gnome and, for the most part, I was able to read and copy files.  Certain directories, however, were not accessible.  While I can't remember the exact permissions on these directories, they wouldn't allow me to see what was inside since I wasn't the owner.  The owner of these directories had a user id (UID) of 501.  I tried using the command chmod to adjust the file permissions but the directory was mounted as read-only.

Why was this partition mounted as read-only?  Is it possible to mount such an hfs partition has read/write instead of read-only using a simple Gnome interface?

I could be way off here, but I'm also assuming that user 501 just happens to be the default user id assigned by mac os x.  If my Ubuntu system had a user with the same user id, would that user suddenly gain ownership of all these newly mounted directories?

---

