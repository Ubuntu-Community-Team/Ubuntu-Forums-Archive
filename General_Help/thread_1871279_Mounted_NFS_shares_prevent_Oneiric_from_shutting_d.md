---
title: "Mounted NFS shares prevent Oneiric from shutting down"
date: 2011-10-28
forum: General Help
---

### Post by ronzo on 2011-10-28
Oneiric does not shut down when there are NFS shares mounted. (this happens on all my clients) If I unmount the shares manually, shutting down works as expected.

Any tips/hints?

Thanks a lot in advance!

---

### Post by Jose Catre-Vandis on 2011-10-28
Not having this problem here,although it does seem to take a bit longer to shut down while it sorts out the network.

How long have you given it? 

What is the nfs version on the server? 

What are you exporting on the server (/etc/exports)?

What is your mount command in fstab (on clients)?

---

### Post by ronzo on 2011-10-29
I gave the system several minutes to shut down - without success.

Here is how i mount the share on the client:
```
server:/srv/smb	/mnt/server/srv/smb	nfs	_netdev	0	0
```

Here is the corresponding exports file on the server:
```
/srv/smb	192.168.1.0/255.255.255.0(rw,no_root_squash,sync,subtree_check)
```

Server and clients run Oneiric 64bit.

How can I tell which NFS version is being used?

---

### Post by Jose Catre-Vandis on 2011-10-29
Try something like this in your fstab(this is most similar to the option set I am using):

```
server:/srv/smb	/mnt/server/srv/smb	nfs   rsize=8192,wsize=8192,timeo=14,intr,bg
```

not sure if you need the _netdev option nowadays, but you can always add it
```
server:/srv/smb	/mnt/server/srv/smb	nfs   _netdev,rsize=8192,wsize=8192,timeo=14,intr,bg
```

You could also try adding the nfs server version (to force v3):
```
server:/srv/smb	/mnt/server/srv/smb	nfs   _netdev,nfsvers=3,rsize=8192,wsize=8192,timeo=14,intr,bg
```

(to force v4 use nfs4 instead of nfsvers=3)

Play around with the options

---

### Post by oldtimer7777 on 2011-10-29
> **ronzo said:**
> Oneiric does not shut down when there are NFS shares mounted. (this happens on all my clients) If I unmount the shares manually, shutting down works as expected.

Any tips/hints?

Thanks a lot in advance!

Have you tried this:

sudo apt-get install ntfs-3g


It doesn't come preinstalled in Ubuntu 11.10, so that could be it.

---

### Post by Jose Catre-Vandis on 2011-10-30
> **oldtimer7777 said:**
> Have you tried this:

sudo apt-get install ntfs-3g


It doesn't come preinstalled in Ubuntu 11.10, so that could be it.

That's for ntf**s** (Windows) partitions and drives not nfs shares. East to get confused ;)

---

### Post by ronzo on 2011-11-21
Using  '_netdev' and 'intr' as options in fstab seemed to help one one system but did not on another.

What could I do to find out what is preventing the system from shutting down? (All I see now is 'Killing remaining processes...   [fail]')

---

### Post by dannytherocker on 2011-11-22
the following was my trick, as root type:


```
cd /etc/init.d && update-rc.d -f umountnfs.sh remove && update-rc.d umountnfs.sh start 19 0 6 .
```

Hope this helps

---

