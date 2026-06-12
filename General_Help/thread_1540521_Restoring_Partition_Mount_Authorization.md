---
title: "Restoring Partition Mount Authorization"
date: 2010-07-27
forum: General Help
---

### Post by Cthulhu_Dreams on 2010-07-27
Normally when you have a partition that isn't mounted, when you try to mount it, it asks you for the root password.

I have two partitions.  One that I wanted mounted at boot, one that I wanted you to have to know the root password to mount.  In the process of trying to setup that one partition to automount at boot, I accidentally changed something (through Pysdm) that made it so the other partition no longer displays that root password verification screen.  Now all it does is give me an error saying I have to be root.  How can I restore that screen?

---

### Post by arrrghhh on 2010-07-27
How are you trying to mount the drive?  I'm assuming you have the one that is mounted automatically thru mounted in fstab and the other one has no entry in fstab?

---

