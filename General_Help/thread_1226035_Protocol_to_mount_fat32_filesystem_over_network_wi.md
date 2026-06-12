---
title: "Protocol to mount fat32 filesystem over network with locking facility"
date: 2009-07-29
forum: General Help
---

### Post by nr0mx on 2009-07-29
I have a fat32 filesystem sitting on a NAS storage device (nslu2) that I need to mount on my Ubuntu system. I've tried Samba and NFS mounts, but both don't seem to support proper locking. More specifically, I am unable to save files to the mounted drive through GNUcash, KeepassX etc, which makes the share fairly useless. 

Is there a protocol that allows me to achieve this ? Note that the NAS storage device is running a linux OS so I can run pretty much any protocol that has a linux implementation. 

The only option I'm not looking for is to reformat the partition to ext3, which I'm not able to do due to other constraints.

Alternatively, has anyone managed proper locking of a fat32 system over the network using Samba ?

---

