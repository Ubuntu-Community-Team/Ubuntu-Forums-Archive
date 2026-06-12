---
title: "Need to increase HDD"
date: 2012-04-20
forum: General Help
---

### Post by napapon on 2012-04-20
HI,

This is my HDD lay out when installed Ubuntu.
My home directory is full but lots of space left in /dev/sda2, how can I access it.

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             19222656   2527440  15718680  14% /
none                   4120976       412   4120564   1% /dev
none                   4125192      1240   4123952   1% /dev/shm
none                   4125192        84   4125108   1% /var/run
none                   4125192         0   4125192   0% /var/lock
none                   4125192         0   4125192   0% /lib/init/rw
/dev/sda1               472036     26121    421544   6% /boot
/dev/sda5             14417392  13036324    648704  96% /home


thanks

---

### Post by jerome1232 on 2012-04-20
You might be able to boot a live cd and shrink /dev/sda2, then move /dev/sda5 back towards /dev/sda2, then grow /dev/sda5 out towards the end disk. It will take a VERY long time.

Anytime you mess with partitions there is a chance something could go wrong so keep a backup handy.

---

