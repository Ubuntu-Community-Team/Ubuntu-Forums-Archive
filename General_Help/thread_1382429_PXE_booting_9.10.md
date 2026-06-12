---
title: "PXE booting 9.10"
date: 2010-01-15
forum: General Help
---

### Post by nikosapi on 2010-01-15
Hi, I've been successfully PXE booting 9.04 for quite some time now. I just freshly set up a bootstrapped version of ubuntu 9.10 to be PXE booted.

The problem is that this new install doesn't boot. It gets stuck with this on the screen "one or more of the mounts listed in etc fstab cannot yet be mounted". It says it's stuck waiting for the root partition to mount (which happens to be an nfs share).

The thing is, if I login at that point the nfs share is mounted and I'm able to access all the files except it's read-only. But if I run "mount -o remount,rw /" then I can use the system like normal.

Why isn't mountall able to take care of this? Does it not support nfs roots?

nick

---

### Post by dcstar on 2010-01-16
> **nikosapi said:**
> Hi, I've been successfully PXE booting 9.04 for quite some time now. I just freshly set up a bootstrapped version of ubuntu 9.10 to be PXE booted.

The problem is that this new install doesn't boot. It gets stuck with this on the screen "one or more of the mounts listed in etc fstab cannot yet be mounted". It says it's stuck waiting for the root partition to mount (which happens to be an nfs share).

The thing is, **if I login at that point the nfs share is mounted** and I'm able to access all the files except it's read-only. But if I run "mount -o remount,rw /" then I can use the system like normal.

Why isn't mountall able to take care of this? Does it not support nfs roots?

nick

Anything that uses Network Manager does not enable full networking until you log in and that GUI app actually starts.

Manually populate the /etc/networks/interfaces file and/or remove the execrable Network Manager package.

---

