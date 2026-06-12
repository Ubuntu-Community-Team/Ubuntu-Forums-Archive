---
title: "Changing Ownership (again)"
date: 2011-11-16
forum: General Help
---

### Post by Quarkrad on 2011-11-16
Running 10.10.  I installed a user **tony** who had access to all drives.  I created another user called **dom**.  I need to change the ownership and permissions of a ntfs partition /dev/sda2 from tony to dom.  I tried sudo chown -R dom:dom /dev/sda2 but when I look at the partition in nautilus it tells that the permissions of sda2 cannot be determined.

---

### Post by Quarkrad on 2011-11-16
Sorted - I think.  Added this to fstab:-

UUID=4B8076424A152808 /media/store ntfs-3g defaults,uid=dom,gid=dom,dmask=002,fmask=113 0 0

gksudo nautilus tells me the owner is dom although normal nautilus still can't determine the owner(???).

---

