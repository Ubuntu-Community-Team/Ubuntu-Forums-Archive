---
title: "Error on connecting external NTFS drive, even though the drive mounts"
date: 2010-05-21
forum: General Help
---

### Post by carn1x on 2010-05-21
Ok, when I turn the external NTFS drive on I get an error popup:

ubuntu Error mounting: mount exited with exit code 1: helper failed with:mount: only root can mount /dev/sdc1 on /media/storage

However even before I click the OK button on the error, the drive pops up in nautilus mounted fine.

I'm guessing that something else is trying to mount it at the same time. It has an entry in /etc/fstab which I put there manually. 

I can't remember if I did anything else that might be causing the error, I'm still at that stage in my linux career where I have to google a ton of guides when I install it and it's not all sunk in yet :)

Thanks for any help :D

---

### Post by dcstar on 2010-05-21
> **carn1x said:**
> Ok, when I turn the external NTFS drive on I get an error popup:

ubuntu Error mounting: mount exited with exit code 1: helper failed with:mount: only root can mount /dev/sdc1 on /media/storage

However even before I click the OK button on the error, the drive pops up in nautilus mounted fine.

I'm guessing that something else is trying to mount it at the same time. **It has an entry in /etc/fstab which I put there manually. **
.......

Putting manual entries for things the system is supposed to do itself always causes problems.

---

### Post by carn1x on 2010-05-21
> **dcstar said:**
> Putting manual entries for things the system is supposed to do itself always causes problems.

Ok, well it didn't do it itself, I don't know of another way to instigate it.

If I remove the fstab entry it just asks for a password every time I plug the external device in, which is less preferable to a pointless error as it requires more work on my part :)

---

