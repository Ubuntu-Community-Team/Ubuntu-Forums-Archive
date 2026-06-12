---
title: "moved partitions around.  start up can't mount a partition now and swap is unallocate"
date: 2012-02-07
forum: General Help
---

### Post by princeofnam on 2012-02-07
I recently had to make more room for my "/" partition.  In the end I had to move my SWAP partition somewhere else.  Ultimately now two errors occur:

1) Upon start up Ubuntu indicates that it can't mount this one partition.  However once I log in I can mount it just fine.
2) My Swap no longer knows which partition of space to use.  How do I allocate that again?

---

### Post by oldfred on 2012-02-07
It seems like you need to update fstab with correct UUIDs or device /dev/sda1 entries.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

# Make permanent mount point (unmount if already mounted):
#If mount points exist, you do not have to create new ones
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

---

