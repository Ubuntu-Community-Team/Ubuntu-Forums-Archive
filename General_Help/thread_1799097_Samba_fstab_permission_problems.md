---
title: "Samba fstab permission problems"
date: 2011-07-07
forum: General Help
---

### Post by lloydwood on 2011-07-07
Hello,

I have spent a long time on this trying various things and haven't got anywhere.

The problem:

I have automounting samba shares setup in my fstab as follows (I've put a false ip, user and password for security):

```
//192.0.0.1/system /mnt/system cifs user=bob,password=1234,rw,dmask=000,fmask=111 0 0
```

This gives me the following permissions on the the mounted share:

```
Dirs:
drwxr-xr-x

Files:
-rwxr-xr-x
```

The permissions I want are rwxrw-rw- but I just can't seem to get them to mount with those permissions. It's an NTFS filesystem on the actual network drive but I'm accessing it through a samba share. The windows side is setup to allow access for all users.

Any ideas?

---

