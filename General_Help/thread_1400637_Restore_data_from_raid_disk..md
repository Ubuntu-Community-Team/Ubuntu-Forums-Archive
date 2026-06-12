---
title: "Restore data from raid disk."
date: 2010-02-07
forum: General Help
---

### Post by orela on 2010-02-07
Hello

I had a raid array (raid 1) in ubuntu 9.04.
I formatted the computer and and installed ubuntu 9.1.
I don't remember the raid name so even if i will install mdadm i don't know what to wirte in x - mdadm --stop /dev/x 
anyway mdadm does not installed on my computer.
I don't want to use the raid any more.
I want that the hard disk will become ordinary without losing the data on it.
This disk is sign as fd partition (linux auto detect) and gparted shows that i have raid disk.
I cannot mount it or any thing else.
How can i remove the raid and use this disk again like an ordinary disk and save the data on it?

Thanks

---

### Post by kidders on 2010-02-08
Hi there,

> **orela said:**
> How can i remove the raid and use this disk again like an ordinary disk and save the data on it?You can't ... at least not easily. The simplest thing to do is install mdadm, mount the raid device & copy the data to another location.

Fortunately, since you were using RAID 1, you're basically guaranteed to have enough disk space to perform the copy. I suggest ...[LIST]
[*]Assemble the array, so you can satisfy yourself it's still in good condition, and that all the disks are in sync. You needn't bother to mount it.
[*]Run fsck on it, to make sure the filesystem is happy.
[*]Remove the redundant disk(s) from the array & mount it (ie in degraded mode).
[*]Now that you can see your stuff is all there, repartition & format the disk(s) you removed & mount them someplace temporarily.
[*]Copy everything on the degraded array to your newly formatted disks. Always use **cp -dpR** (ie don't be tempted to **mv** things, in case something screws up, and you need to start again).
[*]If you're paranoid, force your copied files out to disk with **sync**, before you take the next step, which will make the originals inaccessible.
[*]To stop Ubuntu being clever and attempting to recover your array the next time you boot with any of its disks plugged in, you can destroy the data in the first few sectors of the remaining (degraded) half that you copied your files from. You should unmount & **mdadm --stop** it, and then use **dd** to overwrite the first few kilobytes of the underlying disk partitions. That way, Ubuntu will no longer recognise any of your hard disks as belonging to a RAID array.
[/LIST]

Of course, if you happen to have enough free disk space lying around to simultaneously store *two* copies of everything on your array, life is a bit simpler.

I hope that helps.

---

