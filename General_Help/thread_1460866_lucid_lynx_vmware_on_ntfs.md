---
title: "lucid lynx vmware on ntfs"
date: 2010-04-23
forum: General Help
---

### Post by pacanukeha on 2010-04-23
Hi all,
I'm trying to user vmware player to run an XP vm that is on an ntfs partition. I've enabled the usual entries in the .vmx file:

MemTrimRate = "0"
mainMem.useNamedFile=false
sched.mem.pshare.enable = "FALSE"
prefvmx.useRecommendedLockedMemSize = "TRUE"


And I think my partition is mounted appropriately in my fstab:

/dev/sdb1	/media/windows	ntfs-3g	defaults,noatime	0	0

But launching the vm makes the ntfs daemon take up 100% cpu and the vm is unusable.  The hard drive is an SSD. 6 gigs of ram, 3 GHz dual core machine running an updated lucid lynx 32bit install.  Any thoughts?

---

