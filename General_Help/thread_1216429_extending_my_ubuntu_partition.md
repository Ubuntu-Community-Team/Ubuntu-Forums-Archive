---
title: "extending my ubuntu partition"
date: 2009-07-18
forum: General Help
---

### Post by itachis.eyes on 2009-07-18
ok i have windows and ubuntu dual booted, i used gparted to shrink the windows partition and extend the "extended partition" but now i don't know what to do with the un-used space inside the extended partition...i tryed using the "growfs" command but no...i'm not sure if that is a bash command but all i have to work with is terminal

---

### Post by Rocket2DMn on 2009-07-18
Are you using the [GParted LiveCD]("http://gparted.sourceforge.net/index.php")?  In order to extend Ubuntu's root partition, you need to be on a LiveCD, since you can't change a partition while it is mounted.  You should be able to graphically drag the virtual partitions inside the extended partition to use up the empty space.  If you are having problems, please post some screenshots.

---

### Post by itachis.eyes on 2009-07-18
> **Rocket2DMn said:**
> Are you using the [GParted LiveCD]("http://gparted.sourceforge.net/index.php")?  In order to extend Ubuntu's root partition, you need to be on a LiveCD, since you can't change a partition while it is mounted.  You should be able to graphically drag the virtual partitions inside the extended partition to use up the empty space.  If you are having problems, please post some screenshots.
yes sir, i have the live CD i'll check it out!
******

yep seems to be the way to go thanks

---

