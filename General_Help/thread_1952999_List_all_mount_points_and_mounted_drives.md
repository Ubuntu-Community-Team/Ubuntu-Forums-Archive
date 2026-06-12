---
title: "List all mount points and mounted drives"
date: 2012-04-05
forum: General Help
---

### Post by hojjat on 2012-04-05
Say I have two hard disks (sda and sdb) both mounted, one flash drive which is connected and mounted, and also one remote drive which is mounted using sshfs. Is there a single command that I can run to get a list of all these mount points and where they direct to?

---

### Post by sudodus on 2012-04-05
> **hojjat said:**
> Say I have two hard disks (sda and sdb) both mounted, one flash drive which is connected and mounted, and also one remote drive which is mounted using sshfs. Is there a single command that I can run to get a list of all these mount points and where they direct to?
Yes
```
df
```

---

### Post by Cheesemill on 2012-04-05
Or for a more detailed output:
```
mount
```

---

### Post by Morbius1 on 2012-04-05
Actually, mount will show both partition mounts and those things mounted in other ways like with bind for example. sshfs - if you are using something like nautilus or "connect to server" will not show up specifically. All you will get is a generic "gvfs-fuse-daemon on /home/username/.gvfs" mount refrence.

---

