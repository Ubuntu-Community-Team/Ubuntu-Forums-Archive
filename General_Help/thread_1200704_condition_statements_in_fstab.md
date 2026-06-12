---
title: "condition statements in fstab?"
date: 2009-06-30
forum: General Help
---

### Post by ARhere on 2009-06-30
Hello All,

Is there a way to put condition statements in the fstab file, or delay the running of the fstab file after a network connection has been made?

I keep all my music, pictures, and files on a separate server and our personal computers mount the network drives.  However I have a laptop that does not make a wireless connection until after everything is booted, so network mount comments in the fstab file never work.

Idea's?

-AR

---

### Post by michy99 on 2009-06-30
You can use the mount -a command to mount all the drives in the fstab file if they are not mounted. You just need to put it somewhere it will run as root after the network is connected. I know it can be done, but I don't know the details.

---

