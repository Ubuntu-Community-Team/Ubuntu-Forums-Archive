---
title: "Hard drives in the wrong place"
date: 2009-08-04
forum: General Help
---

### Post by malfist on 2009-08-04
I just finished moving my computer over to a new case and seem to have rearranged my hard drives some how.

BIOS reports it like this:
hd0 : 200GB (call it A)
hd1 : 750GB (call it B)
hd2 : 250GB (call it C)
hd3 : 750GB (call it D)

That exactly how it should be to ubuntu also, but ubuntu reports it like this:

sda is C
sdb is b
sdc is d
sdd is A

The problem is that I have a RAID1 setup, and it's not seeing 'C' anymore. How can I fix this?

---

### Post by malfist on 2009-08-04
Nevermind, mdadm still sees it
mdadm -D /dev/md1 reports:
State: clean
     Number   Major   Minor   RaidDevice State
       0       8       36        0      active sync   /dev/sdc4
       1       8       19        1      active sync   /dev/sdb3


lvm wasn't finding the other crypted swap partition though, I just edited fstab.

I read that mdadm sent mail to root when something went wrong, can I make it send mail to my account instead?

---

### Post by dcstar on 2009-08-05
> **malfist said:**
> Nevermind, mdadm still sees it
mdadm -D /dev/md1 reports:
State: clean
     Number   Major   Minor   RaidDevice State
       0       8       36        0      active sync   /dev/sdc4
       1       8       19        1      active sync   /dev/sdb3


lvm wasn't finding the other crypted swap partition though, I just edited fstab.

I read that mdadm sent mail to root when something went wrong, can I make it send mail to my account instead?

Depending on your MTA, you can configure mail forwarding as you like.

You should be using UUIDs in your fstab file to ensure that particular drives are always identified by the system correctly.

---

