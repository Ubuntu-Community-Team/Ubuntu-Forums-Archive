---
title: "when to check disks"
date: 2011-07-01
forum: General Help
---

### Post by nigeldodd on 2011-07-01
It is quite frustrating to wait on boot for the discs to be checked. Why can't this be done as the machine shuts down instead? It could then switch off after it has completed the checks.

I would not have thought this would be any more difficult to implement than the current (sometimes frustrating) scheme of checking the discs on boot up.

---

### Post by andrewthomas on 2011-07-01
You could always turn it off and check them manually.

---

### Post by haqking on 2011-07-01
> **nigeldodd said:**
> It is quite frustrating to wait on boot for the discs to be checked. Why can't this be done as the machine shuts down instead? It could then switch off after it has completed the checks.

I would not have thought this would be any more difficult to implement than the current (sometimes frustrating) scheme of checking the discs on boot up.


edit your /etc/fstab and you can disable it.

gksudo /etc/fstab

then change the pass column (should be the 6th column)

if you change the value from a 1 to a 0 it will bypass the FSCK

be careful what you do, if you dont know what you are doing dont mess with your fstab

example line in fstab:
UUID=caf56e1d-84af-42cd-9a36-9a02cf4af098    /     ext4    defaults     0       1

the last digit 1, you would change it to a 0

---

