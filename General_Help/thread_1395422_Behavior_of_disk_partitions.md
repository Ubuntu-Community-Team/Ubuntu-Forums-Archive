---
title: "Behavior of disk partitions"
date: 2010-01-31
forum: General Help
---

### Post by pswoo on 2010-01-31
I've used Linux at school, but it's the first time I've had it on my home computer. Have to say that I'm really enjoying Ubuntu so far :).

When I installed, I set my partitions up as follows
|NTFS (Windows) ~25GB| |ext3 (/) ~260GB| |swap (logical) ~2GB | |ext3 ~10GB (/boot)|

Is this scheme going to work, if I want to be able to wipe the last partition and reinstall Ubuntu on the fly without destroying the rest of my files?

I'm also wondering what the effects of re-installing Ubuntu are going to be. What's going to get left behind, with regard to preferences, packages, etc.?

---

### Post by audiomick on 2010-01-31
Hi.
I'm afraid you haven't got it quite right. The important place for user data and user preferences is /home. For a "standard" install that doesn't have multiple Linux versions on the one computer, there is no great advantage in having /boot seperate.
If you want to be able to re-mount your user data and settings, you need to have /home on a separate partition.
The / partition contains, affectively, the OS, and is that which needs to be overwritten in the case of a necessary re-install.

Recommended sizes are
for / : 10 - 15 GB
for swap : as big as RAM if hibernate is required, otherwise around 1GB if swap is bigger than 1GB.

the rest of the space mounted at /home

---

