---
title: "Mount NFS Share"
date: 2010-08-24
forum: General Help
---

### Post by gavinjb on 2010-08-24
Hi,

I am trying to mount a NFS share but the problem seems to be it expects a password (I don't need to supply one in Windows, but then again I have the same username and password for Win Logon as one of the users on my NAS, so that may be why)

When I try and mount it through fstab I get the following error

```

mount.nfs: access denied by server while mounting 192.168.2.150:/Data

```

The fstab entry is as follows
```

192.168.2.150:/Data /media/Data nfs soft,intr,rsize=8192,wsize=8192

```

can anyone see anything I have done wrong in my fstab entry and if not any help in configuring with username and password would be appreciated.

Thanks,


Gavin,

---

### Post by rolnics on 2010-08-24
There's a good HOWTO [here]("http://http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS") on these forums, I used when I was setting up my slug before I got samba working!

Also doing a quick search there's a howto [here]("http://http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html") at Ubuntu Geek which looks the same as above. 

One thing I did read and reminded me, have you setup a /etc/allow and deny file? Also you might want to actually use the IP address of the machine in question in your /etc/exports file rather than the name.

---

