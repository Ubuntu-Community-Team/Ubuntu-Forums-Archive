---
title: "Is this a viable strategy for upgrading ext3 filesystems to ext4?"
date: 2010-01-06
forum: General Help
---

### Post by nerr on 2010-01-06
Hey everybody, I have a sudden terrible urge to upgrade the ext3 filesystems on my home server to ext4.  I don't really have a good reason for doing it other than the fact that I enjoy optimizing and tweaking my system to get the best performance possible from it, and I'd like to try and put some of the skills I have acquired to use.  I have an idea for a relatively easy way to perform this task, but I need some quick reassurance before I go ahead and give it a shot.  Here's the plan:

1) Boot Ubuntu 9.10 LiveCD with server's primary disk connected to the host machine
1) Use tar from LiveCD to make an archive of an entire ext3 partition (these partitions being /boot, /home, and / (root)).  / and /home are 20GB in size, and /boot is 1GB in size.
2) Store said archives on /srv (a very large XFS partition), and make ext4 filesystems on / (root), /home, and /boot.
3) Un-tar the archives from /srv back to their original locations, hopefully creating a seamless transition to ext4 filesystems.  At this point, modify /etc/fstab to ext4 to allow for proper mounting of filesystems next time the server is booted.
4) Run the following commands to add ext4 extents, if this is even necessary after un-taring archives:
```
find /(partition) -xdev -type f -print0 | xargs -0 chattr +e
find /(partition) -xdev -type d -print0 | xargs -0 chattr +e
```

Will this plan work?  If not, is there any way to make it work?  I do have two concerns with the plan though:
1) I had read somewhere that GRUB will not automatically boot from ext4 partitions.  Is there a workaround available which can be done via a LiveCD, or should I simply leave /boot as ext3?
2) Upgrading / (root) seems like it may be a challenge due to the nature of the Linux filesystem (such as hardware "files" stored in /dev and the like), so is there a better approach for this sensitive data than a simple tar dump?

Thanks for the help!

---

