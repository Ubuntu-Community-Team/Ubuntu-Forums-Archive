---
title: "Problem with fstab call on boot 11.10"
date: 2012-03-05
forum: General Help
---

### Post by Robbyx on 2012-03-05
Instead of calling etc/fstab my system has taken to calling etc/fstab:  on startup.

There is an empty directory within etc called fstab: that matches the call but as it is empty, Ubuntu is unable to mount any drives and stops.


I have the etc/fstab file also, but as it is not being called it is being ignored.

Where and how do I correct the script that is running "etc/fstab:" so that I can change it to "etc/fstab" ?

---

