---
title: "Mounting encrypted raid from terminal"
date: 2011-06-04
forum: General Help
---

### Post by lime3k on 2011-06-04
Hi,

I have a RAID array that contains an encrypted volume that I setup using Disk Utility. What I want to do is mount this volume from the terminal and therefore be able to mount at login (as the pass phrase is saved).

At the moment I have to manually click on the volume in Nautilus first before using.

I've been trying to use the following command to no avail: 

```
gvfs-mount -mount /dev/md1
```which simply returns "Error mounting location: volume doesn't implement mount"

Any Help would be appreciated. Thanks!

---

### Post by lime3k on 2011-06-06
is there a terminal equivalent to clicking on a volume in Nautilus, regardless of whether it's encrypted or not?

I'm using 11.04 btw.

---

