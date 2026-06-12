---
title: "Move /home"
date: 2011-11-25
forum: General Help
---

### Post by andy_0 on 2011-11-25
Hi,

I want to move the /home directory to a different partition due to size limitation on my primary partition. Can i simply copy all of /home to the new destination and modify fstab? Is there a possibility to do this "Live" on my system or do I have to boot a Live CD?

If I can not move /home as intented, what choices do I have? Does the OS setup format a partition if I select it as /home or does it just add its content to it?

The current partition is ext4, the new partition where I want to move /home to is btrfs and already mounted (/media/Files).

Regards,

Andy

---

### Post by Azdour on 2011-11-25
Hi,

The Ubuntu Community site has a page on this which should help you:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Although I have done this before I've only ever moved from ext4 to ext4, never moved from ext4 to btrfs.

---

### Post by andy_0 on 2011-11-25
Thanks for the fast reply. Based on the wiki entry it is working and "on the fly" as well.

---

