---
title: "btrfs not really for prime time?"
date: 2010-05-30
forum: General Help
---

### Post by yee379 on 2010-05-30
so i used to be a fuse zfs user; great project btw. however, i was annoyed at the fact that all my nfs mounts on zfs filesystems just hung... all the time. and the amount of memory it was taking up (300MB+?)

so given that i upgraded to 10.4, i figured i'd try out btrfs to see what the fuss was about....

first of all, i think there is really an insufficient amount of documentation with it - both man and online; sure getting it working was easy (but so are most file systems). however, here's a few concerns i have:

- so far i have managed to crash it a few times; first by accidentally unplugging a usb disk drive on a stripe; this completely bjork'd the filesystem and i basically lost everything (even after mount -o degrade, btrfs-vol -r etc)
- none of tools seem to work; nearly everything spits out 'ioctl returns 0' rather than anything meaningful

so should the next ubuntu be on btrfs by default? no - imo.

---

### Post by orlox on 2010-05-30
First: Doesnt this belong in the cafe?

Second: Have you tried btrfs in fedora 13? Unlike ubuntu, they support btrfs as the filesystem to use on installation, and allows some nice features like rollbacks. Perhaps you could find a better experience with a linux distribution that is already into supporting btrfs

---

### Post by yee379 on 2010-05-30
i'm sorry, i was gonna ask for help but then realised that i was basically just annoyed with btrfs ;)

any current problem is that i added a disk to an raid0 array using 'btrfs-vol -a <dev>' and i got 'ioctl returns 0' (a rather cryptic message) - however the file systems looked and worked fine. however, on reboot i can now only (again) mount the file system as degraded. dmesg shows 

```
[  378.777689] device fsid c4b42bcb3a07eea-54441df66d347391 devid 1 transid 8747 /dev/sdf
[  378.778151] btrfs: failed to read the system array on sdf
[  378.800104] btrfs: open_ctree failed

```

now i don't really have extra disk space to copy all the data over (again), anyone know how to fix it?

---

### Post by BoneKracker on 2010-05-30
Even in kernel release 2.6.34, btrfs is marked "Btrfs filesystem (EXPERIMENTAL) Unstable disk format".

The comments say:> Btrfs is highly experimental, and THE DISK FORMAT IS NOT YET FINALIZED

I don't think I'd be too surprised or frustrated by any problems I encountered using it at this stage.

---

