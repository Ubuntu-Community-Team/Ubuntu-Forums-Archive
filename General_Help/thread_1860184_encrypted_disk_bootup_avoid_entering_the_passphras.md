---
title: "encrypted disk bootup: avoid entering the passphrase multiple times"
date: 2011-10-14
forum: General Help
---

### Post by knossos1 on 2011-10-14
Hi,

on a server we have 8 encrypted disks that should be mounted during system bootup.
At the moment for each of the disks there is an entry in /etc/crypttab:
```

disk0 UUID=23423..... none luks

```The disks are then mounted to /mnt/disk0, /mnt/disk1, /mnt/disk2, ....
The passphrase is the same for all 8 disks.

However, when booting the system, one has to enter the same password **8 times** !
Also, we get error messages that several disks can't be mounted as the according devices do not exist yet (since cryptsetup still has to set up the devices).


[LIST]
[*]To avoid this pesky bootup process, how can we change the configuration so that we only have to enter the passphrase** *once*** ?
[*]How can we change the configuration so that the system only mounts the disks, after cryptsetup is finished and the mapped devices exist ?
[/LIST]

As this is a server system, it is highly important that this is done in a **standardized** (i.e. **ubuntu-like**) way.
Due to the high requirement for stability, this is done on the current long term support release of ubuntu (i.e. 10.04).

It is out of question to write custom init scripts or "dirty" hacks that will sooner or later (i.e. after installing upgrades) break the system.
So, what is **the ubuntu-way** to solve this issue in a way that is suited for production systems ?

cheers,
knossos1

---

