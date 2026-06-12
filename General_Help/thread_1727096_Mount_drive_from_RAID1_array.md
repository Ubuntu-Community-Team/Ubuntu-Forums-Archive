---
title: "Mount drive from RAID1 array"
date: 2011-04-12
forum: General Help
---

### Post by Paqman on 2011-04-12
I have a Qnap NAS that has expired and will no longer boot. It's basically a Debian box, and I use two drives in RAID1.

I take a regular backup, but it was a couple of weeks between my last backup and when the box died. So the delta between the data on the array and my backup will be pretty small, but if I can update my backup, that would be good.

How can I plug one of the drives from the array into my Ubuntu machine and mount it so I can rsync to the backup drive? Or do I have to mount them both?

Would I just use:
```
sudo mdadm --assemble /dev/md1 /dev/whatever
```

---

