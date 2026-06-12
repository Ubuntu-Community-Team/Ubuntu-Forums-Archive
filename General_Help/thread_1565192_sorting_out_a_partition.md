---
title: "sorting out a partition"
date: 2010-08-31
forum: General Help
---

### Post by kolo-01 on 2010-08-31
hi, i had a partitioned drive, but now want everything on a single filesystem and so have deleted the partition using administration>disk utility, i now want to extend the capacity of my first filesystem by adding on the space left by the deleted one, is it possible to do this? help appreciated

---

### Post by anoop999 on 2010-08-31
Are you using gparted?
You need to unmount the partition while you resize it.
If it is your main partition, you should back up everything then boot from USB or CD-ROM and run gparted from there.

---

