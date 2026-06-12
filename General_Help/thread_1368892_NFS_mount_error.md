---
title: "NFS mount error"
date: 2009-12-31
forum: General Help
---

### Post by Amelandbor on 2009-12-31
I get an error when I try to mount a NFS share after installing XBMC Live 9.11 (ubuntu karmic).

```
root@XBMCLive:~# mount -a
mount.nfs: mount to NFS server '192.168.1.8:/Disk1' failed: RPC Error: Program not registered
```

This is my fstab file

```
# synology
192.168.1.8:/Disk1 /home/xbmc/Disk1  nfs rsize=8192,wsize=8192,timeo=14,intr,bg
192.168.1.8:/Disk2 /home/xbmc/Disk2  nfs rsize=8192,wsize=8192,timeo=14,intr,bg
```

---

### Post by Amelandbor on 2009-12-31
Nevermind, the ip was from the machine itself not from the NAS ](*,) ](*,) ](*,)

---

