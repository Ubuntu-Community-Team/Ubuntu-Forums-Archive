---
title: "Mount shared ext3 drive on boot"
date: 2009-10-14
forum: General Help
---

### Post by prem1er on 2009-10-14
I know I have seen tutorials for this before, but I can't seem to find them  now.  I need to mount an ext3 drive from my ubuntu server to my 9.10 laptop. Can anyone explain this or have a good link for me? Thanks.

---

### Post by prem1er on 2009-10-15
bump.

---

### Post by louieb on 2009-10-15
I use nfs 
Basically install nfs server on the server and nfs client on the client.

on the server edit /etc/exports to define what you want to share heres mine


```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/media/backup   10.0.0.0/255.255.255.0(rw) 
/media/stuff    10.0.0.0/255.255.255.0(rw) 
/home           10.0.0.0/255.255.255.0(rw) 
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#


```Then on the client mount the share - can be done in fstab but it needs to be connected so I use a script. I'd show it too, but I'm on the server now and can't get too it. lol guess I need to put copy on the server too.
More here [HOWTO: NFS Server/Client - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs")

---

### Post by prem1er on 2009-10-15
Thank you. I already have samba installed on the server to share the drive with my Windows machine, could I just use that to share, instead of using nsf?

---

### Post by louieb on 2009-10-15
You can use Samba, but compared to nfs its a pain in the butt. Thats why I quit using samba.  

See if this helps [HOWTO  Setup Samba peer-to-peer with Windows - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=202605&highlight=server")
its 3 years old there may be a newer gui way.

---

### Post by alphaniner on 2009-10-15
I would recommend [this thread]("http://ubuntuforums.org/showthread.php?t=288534&highlight=samba") instead.  I think it's what I used to learn how to auto mount samba shares through fstab.

---

