---
title: "cloned drive and now cant resize my ubuntu partition?"
date: 2009-10-29
forum: General Help
---

### Post by sdowney717 on 2009-10-29
i cloned my drive using the maxblast software. everything is there on the new drive. I thought i could use gparted in a live cd to make it bigger, 
but it wont let me make it bigger.
so what do i do?, it is not mounted.

well apparently you have to have free space to the right of it.
so i first deleted the swap partition
then i  increased the sda2 exteneded 
then i increased the sda5 ext4

question, why is sda5 contained within sda2 extended?

---

