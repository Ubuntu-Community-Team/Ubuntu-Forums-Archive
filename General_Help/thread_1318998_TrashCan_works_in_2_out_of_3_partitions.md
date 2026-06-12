---
title: "TrashCan works in 2 out of 3 partitions?"
date: 2009-11-08
forum: General Help
---

### Post by irishbreakfast on 2009-11-08
On my laptop I have the following partitions. If I put files in /dev/sda5 or /dev/sda6 and delete them using nautilus, they go into the trash can.  

/dev/sda8 / ext3 rw,errors=remount-ro 0 0
/dev/sda5 /home ext3 rw 0 0
/dev/sda6 /xfer ext3 rw 0 0

The problem is when I delete files on /dev/sda8 they don't get moved to the TrashCan. I have moved my music files from /dev/sda5 to /dev/sda8 and changed the owner and the group. It was when I started deleting music I no longer wanted that I was surprised to get the pop up saying that the files can't be moved to the Trash Can, I can only delete them.

from ls -la /
drwxr-xr-x   8 myusername myusername  4096 2009-11-08 20:39 Music 
drwxr-xr-x   4 myusername myusername  4096 2009-11-08 20:39 xfer

Can anyone explain this behaviour?

---

### Post by irishbreakfast on 2009-11-10
bump. Please...

---

