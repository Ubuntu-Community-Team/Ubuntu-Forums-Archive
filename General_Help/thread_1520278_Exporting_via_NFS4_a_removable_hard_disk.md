---
title: "Exporting via NFS4 a removable hard disk"
date: 2010-06-29
forum: General Help
---

### Post by MadMageX on 2010-06-29
I have a laptop with a xubuntu distro (but I think it's not related to xubuntu at all): an external Hard Disk is connected via USB to this laptop: xubuntu mounts that in /media/Ganesh, the owner is ska (my user) and the group is root, but the permissions are rw only for ska, nothing for the group nor for the others.

I want to export the external hard disk using nfs4: for this reason, I mounted it on /export as /export/Ganesh, using
# mount --bind /media/Ganesh /export/Ganesh

That directory (/export/Ganesh) has the same permissions of the /media/Ganesh (I think this is obvious.

Now, I have another laptop where I mount that filesystem using the following:
# mount -t nfs4 192.168.x.x:/ /mnt/nfs/pc01

Unfortunately, the directory /mnt/nfs/pc01 contains only a directory Ganesh that is EMPTY... I think that this is related to the fact that on the initial PC, the device is mounted with "ska" ownership, and nobody (root neither, who remounted and exported the filesystem) can do anything with that.

Trying to change the ownership of /media/Ganesh or of /export/Ganesh has no effect.

How to solve this?

Thanks!

---

