---
title: "Grub2 persistent partition"
date: 2011-01-04
forum: General Help
---

### Post by randiroo76073 on 2011-01-04
Hi all, I've read and read & am still no smarter. I've tried to make a persistent partition(one that mounts whenever I boot/login). Either I don't have the right file or syntax, I've given up and need help. Please tell me exactly which file to edit and the proper syntax to put there. The partition on my machine I want to do this for is "sdb2" uuid "02f5852a-c3e2-47e8-b1dd-93592f1f87ee" label "archives"
Any help will be greatly appreciated, I'm almost bald now...LOL!

---

### Post by ridgeland on 2011-01-04
What do you mean?
mount during boot as in /etc/fstab?
GRUB2 always on the same partition?

---

### Post by hawkmage on 2011-01-04
I assume that the drive will be attached at boot time.  To mount the drive automatically add a line to the /etc/fstab (Make a backup before modifying it)

The line would be something like this:
```
UUID=02f5852a-c3e2-47e8-b1dd-93592f1f87ee /DirToMountAt ext4 defaults 0  2
```
Just replace the "/DirToMountAt" with the location you want it to be mounted, the directory should be empty.  Also if the filesystem is not ext4 you will have to change the ext4 in the line to match the filesystem on the drive.

---

### Post by randiroo76073 on 2011-01-04
Thanks very much for the help Hawkmage, I was getting short tempered with the wall on this one...LOL!

---

### Post by randiroo76073 on 2011-01-05
I'm not sure why, but that infomation doesn't show up in any of the tutorials I've read or threads/posts either. I had gathered from when Grub2 first came out that it didn't pay any attention to fstab anymore, which,in my interpretation made fstab irrelevant.

---

### Post by hawkmage on 2011-01-05
Because it has nothing to do with Grub at all.  Grub is the boot loader while the /etc/fstab is what is used during the init process to get all of the services up and running.

---

