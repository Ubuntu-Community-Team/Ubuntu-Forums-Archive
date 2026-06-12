---
title: "Automount NTFS like Gnome does?: mount is owned by the user, not root"
date: 2011-04-04
forum: General Help
---

### Post by hoink on 2011-04-04
(This is a clarification to a previous question.)

When I mount my NTFS via Gnome, the owner, group and permissions for the mount point are set for *me* (the user doing the mounting), not root.

How can I make this occur automatically upon login?

(ntfs-config assigns ownership to root.  all the HOWTOs out there with fstab do the same.)

---

### Post by lithopsian on 2011-04-04
Partly this will depend how you are mounting the drive, but assuming a local drive try putting the user (or users) option in fstab.  This does funny stuff sometimes, but it *should* do two things for you.  It should let any user mount the drive and the person who mounts it should become the owner.  Depending on when the mount is done this might still be root!  You may have to change when the drive gets mounted.

---

### Post by QLee on 2011-04-04
[QUOTE=hoink]...
(ntfs-config assigns ownership to root.  all the HOWTOs out there with fstab do the same.)[/QUOTE]
This one does not appear to do the same. Will it work for you?
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by hoink on 2011-04-04
Not really, but I solved my problem another way.  Thanks.

---

