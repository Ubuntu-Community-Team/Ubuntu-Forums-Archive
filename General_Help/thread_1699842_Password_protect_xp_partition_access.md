---
title: "Password protect xp partition access"
date: 2011-03-04
forum: General Help
---

### Post by flyerbrooks on 2011-03-04
Hi all
I am currently running Lucid 10.04(lts) on a dual boot with windows xp. What i am looking for is some guidance on how to re-install the requirement for a password when trying to mount the xp partition as this was standard in Jaunty and i liked it like that as my computer is often open for many hours at work. Yeh i know i can lock the screen but sometimes other people need to use my computer.
Any help would be very much appreciated.
Flyer

---

### Post by Smart Viking on 2011-03-04
Remove it from fstab, so root privileges is required to mount.

---

### Post by flyerbrooks on 2011-03-04
Not sure which way to go with this as i see no reference to my xp partition, only the swap and ext4 partitions.

---

### Post by QLee on 2011-03-04
Well then, put a stanza for it in fstab and use the mount option, "noauto", that way it will not be mounted at boot time or automounted but available for manual mounting when you want it mounted.

---

### Post by flyerbrooks on 2011-03-05
Thanks for all help, its been appreciated but im not really familiar with the fix mentioned. I think this one is a little above me right now. Cheers

---

### Post by QLee on 2011-03-05
> **flyerbrooks said:**
> Thanks for all help, its been appreciated but im not really familiar with the fix mentioned. I think this one is a little above me right now. Cheers

Sorry, because you posted in General Forum I thought a hint would be enough.

What I meant was using the, "noauto" option in the fourth field, (filesystem mount options) on the line for that filesystem in fstab. This documentation can explain it in detail, probably the first post is enough:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by flyerbrooks on 2011-03-17
Thanks for all submissions, i will work through it from here.
Appreciate it :-)

---

