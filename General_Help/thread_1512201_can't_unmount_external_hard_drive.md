---
title: "can't unmount external hard drive"
date: 2010-06-17
forum: General Help
---

### Post by venicequeen7706 on 2010-06-17
I have an external hard drive which connects to a usb port. until recently i could unmount it by right clicking on the desktop icon and selecting unmount. now when i try that it tells me that i can't because the device is not in fstab and i am not the root. i checked mtab and it had this line
'/dev/sdb1 /media/usb0 msdos rw,noexec,nodev,nosuid 0 0' i changed that to 
'/dev/sdb1 /media/usb0 msdos user,rw,noexec,nodev,nosuid 0 0' thinking that would fix it, but it didn't. i unmounted using 'sudo umount /media/usb0' and restarted my computer and now the line in mtab reads
'/dev/sdb1 /media/usb0 vfat rw,noexec,nodev,sync,noatime,nodiratime 0 0' and i still can't unmount without using the sudo umount command. i also tried adding '/dev/sdb1 /media/usb0 msdos user,rw,noexec,nodev,nosuid 0 0' to fstab and that didn't help

---

### Post by dhughes on 2011-03-09
Why is this marked solved?

 There isn't any information how this was solved for anyone who comes across this post.

 "Solved" should be removed or this post should be deleted to prevent false leads when Googling this problem.

---

### Post by venicequeen7706 on 2011-09-12
> **dhughes said:**
> Why is this marked solved?

 There isn't any information how this was solved for anyone who comes across this post.

 "Solved" should be removed or this post should be deleted to prevent false leads when Googling this problem.
It's marked solved because it is no longer a problem for me, therefore the problem has been solved. there is no description of how because i'm not sure how or why it started working

---

