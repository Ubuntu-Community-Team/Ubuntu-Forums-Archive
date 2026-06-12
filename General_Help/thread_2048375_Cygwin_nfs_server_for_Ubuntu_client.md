---
title: "Cygwin nfs server for Ubuntu client"
date: 2012-08-26
forum: General Help
---

### Post by Gulyan on 2012-08-26
I want to setup a nfs server on windows(desktop) and use ubuntu(laptop) as the client.

I've installed cygwin and nfs-server on windows, but I can't mount anything from linux.

The /etc/export from cygwin contains:
```

/mnt/d 192.168.0.100(ro)
```

On my laptop, I get the following result with showmount:

```
showmount -e 192.168.0.101
Export list for 192.168.0.101:
/mnt/d 192.168.0.100
```

If I try to mount, I get this:

```
sudo mount -t nfs  192.168.0.101:/mnt/d d
mount.nfs: Connection timed out
```

If I put a * in /etc/exports I get this:

```
sudo mount -t nfs 192.168.0.101:/mnt/d d
mount.nfs: access denied by server while mounting 192.168.0.101:/mnt/d

```
Please help :(

---

