---
title: "Uninstall Ubuntu, but keep partion size and GRUB"
date: 2010-08-10
forum: General Help
---

### Post by sansa90 on 2010-08-10
I tried to upgrade from 8.10 to 9.04 yesterday as a newbie. Trouble is half way through, my computer froze so I had to hard shutdown. Bad idea, right?

anyways, I get back onto it, and the only way I can use ubuntu is through failsafe xterm. It tells me to fix my system. To bad I don't know how. So, right now, I've got a CD for 9.04, but I need to get rid of my 8.10 partition, but keep GRUB and the partition space. Does anyone get what I'm saying? If so, can you help me? If not, I can try to clarify. Thanks in Advance, Sansa90

---

### Post by oldfred on 2010-08-10
Do you want to try to repair your current install or just do a new clean install. Do you have a separate /home? Have you good backups of /home, custom settings in /etc that are system wide and a list of installed programs.

To repair you can chroot from the liveCD into your system and run repairs. If install was mostly done this may work.

If you have to do a new clean install you can still copy /home but I do not know how to get the other data from a broken system other than the chroot fixes. Do you have extra space on your hard drive to install another system partition? You would need 10-20GB for a new system partition.

---

### Post by sansa90 on 2010-12-07
I'm fine with doing a new, full install. What I want to do, if it is possible is to erase all the Linux data on the Linux partition, but keep the amount of room in the partition to put a new edition of Linux onto that space.

---

