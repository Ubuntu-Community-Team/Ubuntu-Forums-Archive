---
title: "reload &quot;df&quot; information?"
date: 2011-11-24
forum: General Help
---

### Post by tunefish85 on 2011-11-24
Hi there,

I have a Ubuntu 10.04.3 x64 server running with hotswap drives.
Everything is fine with the hotswap, swap out, xswap in, remount - everything cool :)

but, as you know, everytime you plug in a drive it gets a new /dev/sd* name, but the old still exists.
And this results in a copy of my drive in the output of "df -h" every swap... :/
Tried command "sync" and this even removed the old sd* from /dev/, but df doesn't care and still displays the old partition information.

do you know how to reload the information that df displays, so that it forgets the "old" /dev/sd* links?

I use df for my own drive usage display on a webinterface, that only displays my backup volumes... so i need to make sure this information is up to date...


Thanks
Chris

---

### Post by regala on 2011-11-24
> **tunefish85 said:**
> 
do you know how to reload the information that df displays, so that it forgets the "old" /dev/sd* links?


well, df uses the content of /etc/mtab to know what is mounted where, and /etc/mtab is edited by mount when it sees fit.
and if no /etc/mtab, it uses /proc/mounts which is *not* editable, and which is handled by the kernel.

---

### Post by tunefish85 on 2011-11-24
hm, good point you brought there,
i actually do have 3 mounts to the same mountpoint after swapping one drive 2 times.
but trying to umount the old references doesn't work at all...

```
umount /media/drivename
```
simply does nothing

and
```
umount /dev/sd<old>1
```
return an error
```
umount: cannot umount /dev/sd<old>1 -- /dev/sd<new>1 is mounted over it on the same point.
```

---

### Post by tunefish85 on 2011-11-24
maybe i should do something like that:

in my udev initiated script where i mount the drive, i could first grep mount for the target location and if it's still there, i umount it before mounting the "new" device...?

EDIT: No way, my udev script doesn't know the "real" mountpoint at that time - fstab does it for me -.-

---

