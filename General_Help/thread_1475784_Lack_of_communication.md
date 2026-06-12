---
title: "Lack of communication?"
date: 2010-05-07
forum: General Help
---

### Post by 98cwitr on 2010-05-07
So I rebooted my machine last night and upon plymouth splash (which was responsive) my HD was pegged for about 10 minutes, I made the assumption that it was running a fsck so I left it alone. After about 10-15 minutes it was done and my desktop appeared. 

Are you guys getting notification of a fsck? In 9.10 and prev, before splash I would get a notification of such an event...now nothing...or maybe it was something else :?

---

### Post by dino99 on 2010-05-07
notification is still there but not often seen

sudo shutdown -F -r now (force a fsck on next reboot)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure plymouth

---

### Post by byStanderone on 2010-05-07
...haven't encountered an fsck without notification as of yet, unless there's a hide option somewhere which 'am not aware of.

---

### Post by 98cwitr on 2010-05-11
> **dino99 said:**
> notification is still there but not often seen

sudo shutdown -F -r now (force a fsck on next reboot)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure plymouth

will run tonight...thank you.

---

