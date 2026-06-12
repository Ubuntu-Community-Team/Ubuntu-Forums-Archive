---
title: "Btrfs on External Drive - User create files/subvolumes?"
date: 2010-01-14
forum: General Help
---

### Post by victorhooi on 2010-01-14
heya,

I'm trying to get btrfs setup on an external USB HDD.

I've created the btrfs filesystem on the disk, and automatically mounted the volume using Device Notifier (hal).

However, I'm unable to write or create new snapshots/subvolumes using my ordinary user account, I have to sudo for that. I can change the owner of btrfs subvolumes (folders) to my users to allow them to write to just that folder, but I still can't create anything in the root. I tried changing the owner of the folder in /media (i.e. /media/volume_name) to my user, that didn't work (and I don't think I should be doing that, right?)

I'm wondering how I can set it up so that ordinary users (either just my account, or a list of them) can seamlessly write to the root of the volume, or create new snapshots/volumes?

Cheers,
Victor

---

### Post by rockorequin on 2010-02-07
I got read/write to the root btrfs folder working by doing sudo chmod 755 /media/<mounted foldername>. (I first changed the owner to my own user, which didn't work, so the folder is also owned by my user whenever it mounts). I can now write to the root of the drive and also run btrfsctl -s without sudo to create snapshots (although btrfsctl -D won't let me delete them).

On a related note, the drive mounts fine the first time, but if I remove it, plug in another drive, and remount the btrfs drive so it changes device, I can no longer mount it. For instance, if the btrfs partition mounts as /dev/sdb1 the first time, and /dev/sdc1 the second time, the system reports that it can't read the superblock. It appears to still be trying to read /dev/sdb1, because if I remove both drives and plug in the btrfs drive again so that it becomes /dev/sdb1, it mounts just fine. If I reboot, it mounts just fine as /dev/sdc1 (or any other device) the first time. Have you seen this?

---

