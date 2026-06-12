---
title: "Allowing users to view ntfs partitions"
date: 2006-02-07
forum: General Help
---

### Post by jackrabbit123 on 2006-02-07
No matter what I do I can't get to a point where I can view a ntfs partition as a non-root user.  I changed the group of the directory to users, changed my fstab to allow users to [un]mount, and changed permissions on the directory to 555 (r-x for everyone).  Then I realized that no matter what I changed the directory to, it reverted to dr-x------ root root once I mounted the partition, even as a non-root user.  I've never experienced this before (been using linux since 1999) although I've also never mounted an ntfs partition before.  I don't know if the ntfs partition is causal or not.  If anyone can figure this you'll be my hero (almost).
Thanks,
Chris

---

### Post by davidstep on 2006-02-07
Try this,
[http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only]("http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

---

### Post by aysiu on 2006-02-07
That's a good guide, but it also assumes your NTFS partition is at /dev/hda1 (which it might not be) and that you're using Gnome, which you're clearly not. See the fourth link of my signature instead--it walks you through step by step.

---

### Post by FlakJacket on 2006-02-07
I used your guide aysiu a couple of days ago.  Excellent guide, works perfectly.  I wanted to PM you thanking you but you have them disabled so thank you.

Flak

---

