---
title: "change disks from Raid 0 to Raid 1"
date: 2011-12-01
forum: General Help
---

### Post by p2ranger on 2011-12-01
I don't know how I did it, but back when I set up my server, I made my raid array 0 instead of 1. I want to have my two disks running raid 1 as exact copies instead of spreading the love amongst the two. I have a backup disk (the same size as each individual disk in the array) I've been rsyncing to, so its up to date.

Can this change be done fairly easily? I only have command line access to my server. I'm guessing it will erase what's currently on the array, but I can live with that because of the backup disk.

Thanks

Jason

---

### Post by p2ranger on 2011-12-12
I'm trying to get rid of the current array to build a new array with the same disks. (Going from type 0 to type 1). These two disks that are in the array just hold data. The OS is running on a separate physical disk. I can not get the current array to stop. I keep getting:

```
mdadm: fail to stop array /dev/md0: Device or resource busy
```

I was getting similar problems with trying to just unmount it. I terminated all of the processes I could find that were associated with using the array, but it still wound't unmount. Using fuser /dev/md0 returns nothing. Using webmin, I was able to find that [md0_raid1] was still running. I couldn't ever get it to stop.

I found a command that did unmount it:
```
sudo umount -l /dev/md0
```

Now that its unmounted, I can't get the array to stop.

```
sudo mdadm --stop /dev/md0
mdadm: fail to stop array /dev/md0: Device or resource busy

```

I don't know what to do now? The tutorial I am following:
[http://www.tcpdump.com/kb/os/linux/removing-raid-devices.html]("http://www.tcpdump.com/kb/os/linux/removing-raid-devices.html")
mentions using fuser to see what may be running on the array, but as I said before, nothing shows up after I enter fuser /dev/md0

Thanks for any help

Jason

---

### Post by p2ranger on 2011-12-13
bump

---

### Post by zero2xiii on 2011-12-13
Hay,

It seems like this is a difficult task. One idea I just have to poke in your direction, use a SECONDARY system. In other words a live or something simmilar to re-setup everything. I have a feeling you may need to redo everything from scratch, as this is going to leave a LOT of residual configs and may cause instability.

Very good luck though.
Cherz

---

