---
title: "Running out of hard drive memory on ubuntu"
date: 2012-06-24
forum: General Help
---

### Post by tooXfit on 2012-06-24
i have a partition of my hard drive that has 300 gigs of memory left but i cant access any of it on ubuntu. when i go to the home folder it says i only have 11 gigs of memory left. how do i get memory to be accessed on ubuntu

---

### Post by oldfred on 2012-06-24
Is this a wubi install?

Post these from terminal.

sudo fdisk -lu


Click on any partitions not mounted first as this only shows mounted partitions.
df - H

---

### Post by Cheesemill on 2012-06-25
Posted in wrong thread.

---

