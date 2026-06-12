---
title: "I can't get hibrinate to work in LVM installation."
date: 2010-12-16
forum: General Help
---

### Post by BurningSludge on 2010-12-16
I Installed Ubuntu 10.04 with Logical Volume Management last month and then upgraded to Ubuntu 10.10 and noticed that I have been loosing power faster than I have been used to. I have realized that I didn't have a hibernate option. I should be able to hibernate because I have over 5 GB LVM swap partition  and only 2 GB of ram on my Laptop. How do I get the hibernate feature back?


EDIT the original installation was with encrypted home but I moved off of the encrypted home.

---

### Post by BurningSludge on 2010-12-16
I had to configure /etc/fstab and add a known swap device from /dev/*name of your system*/*name of your swap device*.

---

