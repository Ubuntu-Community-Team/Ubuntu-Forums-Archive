---
title: "Considering LVM for desktop"
date: 2009-11-03
forum: General Help
---

### Post by AnomalyDetected on 2009-11-03
I generally prefer to do fresh installs with each new release as opposed to an upgrade, but the whole backup and reinstall process does get tedious.

So I've been reading up on LVM to help make the changeover to future releases easier, and now I've got a couple of questions and to how this is going to work next time.

So I've got one physical disk on a test box and have set up /dev/sda1 as an ext3 partition of 100M for my /boot mounting point.

/dev/sda2 is the LVM partition consuming the rest of the drive and contains several logical ext4 volumes for /, /home, /usr and a swap.

Karmic is installed and working with the above. But let's say Ubuntu 10.4 comes out down the line and I want to do a fresh install of it, but keep my /home and /usr. How exactly would I go about this? Do I create a new / (root) volume, install the cd to that, and use that as the new / mount point?

---

