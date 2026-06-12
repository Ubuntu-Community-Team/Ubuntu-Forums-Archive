---
title: "Mount XFS Partition with permission"
date: 2006-06-03
forum: General Help
---

### Post by funnyguyfunnyguy on 2006-06-03
I apologize if this is already in the forums somewhere.

How do I mount an XFS partition to /media/documents so that I have read/write/execute permission?

I already have the partition mounted, and it loads at start up. I have looked into the chmod and chown commands but don't really understand what's going on with them.

Thanks for any help.

---

### Post by BoneKracker on 2006-06-03
go to the console and type

man fstab
(read that)

man mount
(read that)

and you'll know what to do

---

### Post by disturbed1 on 2006-06-03
Put something like this in your fstab

/dev/hdz8   /media/documents   xfs   defaults   0   0

of course /dev/hdz8 is your actual drive that needs to be renamed.

You have to chmod a dir when it isn't mounted.
then you could sudo nautilus, browse to the folder, and set the perms to your user group and owned by you. Or sudo chmod a+rwx /media/documents to add read write and execute perms for all users.

---

