---
title: "Mounting Errors"
date: 2009-10-04
forum: General Help
---

### Post by Inaia on 2009-10-04
I buggered up my Windows XP partition today by changing a couple of settings, and would like to know if there's a way to undo them without reinstalling Ubuntu / XP.

Changes (both made in the partition's Properties):
-Mount Point changed to /media/ice 
-File System specified as NTFS

Errors when trying to mount:
-Cannot mount volume.
  Error org.freedesktop.Hal.Device.UnknownError
  libhal.c 1399 : wrong reply from hald. Expecting an array.
  org.freedesktop.Hal.Device.PermissionDeniedByPolicy

-Unable to mount location
  DBus error org.freedesktop.DBus.Error.NoReply: Did
  not receive a reply. Possible causes include: the
  remote application did not send a reply, the reply
  timeout expired, or the network connection was
  broken.

---

### Post by abhilashm86 on 2009-10-04
i suggest you use ntfs-config tool to correct and mount that partition, [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by Inaia on 2009-10-04
Rawr! Thanks, it worked! <3  Not only did it FIX the damage, it even made it auto-mount on boot.....epic <3 You win a free bag of popcorn for your effort :popcorn:

~bookmarks that HOWTO~

---

### Post by abhilashm86 on 2009-10-04
> **Inaia said:**
> Rawr! Thanks, it worked! <3  Not only did it FIX the damage, it even made it auto-mount on boot.....epic <3 You win a free bag of popcorn for your effort :popcorn:

~bookmarks that HOWTO~

accepted popcorn:), mark thread as solved,go on......

---

