---
title: "Access only one folder on ntfs drive"
date: 2009-07-02
forum: General Help
---

### Post by Konomics on 2009-07-02
Hi all,

I have duel boot computer with Vista and Ubuntu 9.04 installed. I want to have the windows ntfs partition mounted when Ubuntu boots so that I can share a folder on my home network. The problem is I don't want normal users (and especially not the guest user) to have full access to the ntfs partition. All the stuff I've read so far seems to say that you either give full access or no access.

Any ideas? Is this possible?

---

### Post by blueridgedog on 2009-07-03
You may apply a single owner only to an ntfs drive.  That is the owner who mounts the drive or the owner specified in the mount command using the uid=xxxxx,gid=xxxxx syntax.  If you want folder level permissions, you need to use a native linux file system.

One way around this is to accept that the local user (on the Ubuntu system) will have access, but control your access via samba to those on the network.

If the drive is mounted at:  /mnt/ntfsdrive and the folder of interest is /mnt/ntfsdrive/folderIshare, then you can create a network share for just that path and location.

---

### Post by Konomics on 2009-07-03
Hmm, is it possible to deny access to the mounted partition for every user except root on the Ubuntu machine? Would that then allow root to share only specific folders to other users via the network?

I think you might be saying that I can't so, like you said, I'm just going to have to accept it.

---

### Post by blueridgedog on 2009-07-03
It is worth testing.  Root can mount and own the drive, then share out specific folders with specific samba permissions.

---

