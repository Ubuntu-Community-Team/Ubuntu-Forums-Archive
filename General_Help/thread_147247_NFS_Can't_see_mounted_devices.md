---
title: "NFS: Can't see mounted devices"
date: 2006-03-19
forum: General Help
---

### Post by luckSpray on 2006-03-19
Hi!

I've managed to get a NFS server up and running but there's one problem; I'cant see the additional HD, the FD and the CD-Rom drives of the NFS server. They are mounted in the mnt dir (I know Ubuntu Standard for mounted devs is media but I like mnt more ;), and I can see them if I login to the server via ssh.

nfsserver:/etc/exports
```

/ 192.168.0.111(rw,no_root_squash)
#/mnt/hdd0 192.168.0.111(rw)
#/mnt/hdd1 192.168.0.111(rw)

```

nfsserver:/etc/fstab (excerpt)
```

/dev/hdb1    /mnt/hdd0      ext3        defaults        0       0
/dev/hdc1    /mnt/hdd1      ext3        defaults        0       0

```

client:/etc/fstab (excerpt)
```

192.168.0.100:/ /mnt/nfsserver     nfs      rw,hard,intr,rsize=8192,wsize,8192      0       0

```

As you can see I've exported the whole filesystem. If I export the mountpoints explicitly (like in the comments in /etc/exports) everything works fine. But I don't like to mount each mounted device of each NFS server explicitly.

I don't know if this is somehow an intended function or simply a trivial matter of permissions or something and I didn't find anything about it. IMHO it's a very strange behaviour because I thought every device is totally abstracted to this filesystem and therefore NFS shouldn't care about the hardware underlying the filesystem.

Help is really appreciated!
Thanks in advance.

---

### Post by colo on 2006-03-20
NFS is indeed supposed not to care about the physical structure of the device underlying its exported filesystems - I don't know what's going on on your box either, but I must warn you:

You SERIOUSLY impaired your system's security by exporting / without supplying AT LEAST root_sqaush (or better yet, all_squash!). If the network your shares are exported on is anywhere near open or untrusted, your system may likely be compromised or destroyed.

---

### Post by luckSpray on 2006-03-20
[QUOTE=colo]You SERIOUSLY impaired your system's security by exporting / without supplying AT LEAST root_sqaush (or better yet, all_squash!). If the network your shares are exported on is anywhere near open or untrusted, your system may likely be compromised or destroyed.[/QUOTE]

I'm aware that this would be a security issue if there's someone I don't trust. But I was just messing around with NFS and the only user using this network is me.

Original problem persists :cry:

---

### Post by AndyCooll on 2006-03-20
In your client /etc/fstab what happens if you change the permissions etc to "defaults"?

---

### Post by luckSpray on 2006-03-20
[QUOTE=AndyCooll]In your client /etc/fstab what happens if you change the permissions etc to "defaults"?[/QUOTE]

Just tried that. But I still can't see them...

---

### Post by luckSpray on 2006-03-23
Anybody got an idea?

I'm still stuck with this one and can't figure it out. I've asked many people in the meantime to no avail...

:-k

---

