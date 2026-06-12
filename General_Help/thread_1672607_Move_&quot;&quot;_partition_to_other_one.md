---
title: "Move &quot;/&quot; partition to other one"
date: 2011-01-21
forum: General Help
---

### Post by kubad_cz on 2011-01-21
Hi all,

My problem is that I have small size on my current partition mounted as / so I would like to move it to other partition. Is here anybody who has experience with moving / partition?

My plan is: load Live CD and copy all files from current partition to second one and then change settings in /etc/fstab.

Do you think it would work?

Jakub

---

### Post by bikodog on 2011-01-21
i had the same problem once before too.

The best solution I found was to backup /home and any other data and then just do a fresh install.

It's for this reason that having /home on a separate partition is so advantageous. If a need arises to change the root partition, you can always fall back to format / and reinstall the distro.

---

### Post by dandnsmith on 2011-01-21
> **kubad_cz said:**
> Hi all,

My problem is that I have small size on my current partition mounted as / so I would like to move it to other partition. Is here anybody who has experience with moving / partition?

My plan is: load Live CD and copy all files from current partition to second one and then change settings in /etc/fstab.

Do you think it would work?

Jakub

You haven't said anything about your current HDD organisation (how many partitions, what sizes) or even whether the new copy is to be on a separate HDD, so the question is a bit open ended.

There are quite a few pitfalls, and these can be situation dependant.
I've done this sort of thing using gparted (not from the current installation - on a CD or otherwise) - where you can extend the partition, copy it .... It does, however require a bit of knowledge, so you can sort out any ensuing problems about booting and so on.

---

