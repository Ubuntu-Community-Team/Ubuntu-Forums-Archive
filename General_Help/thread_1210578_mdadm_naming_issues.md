---
title: "mdadm naming issues"
date: 2009-07-11
forum: General Help
---

### Post by KCormier on 2009-07-11
I'm using mdadm to create a software raid of 2 drives.  Right now I'm tesing in a virtual machine (virtualbox 3 with ubuntu server 9.04).  I have 3 small hard drives.  An 8 gig with ubuntu installed on it on just a regular ext3 partition.  The other two are just 2 gig drives.

I create /dev/md0 and add them to it, but after a restart, running

cat /proc/mdstat

always show /dev/md_d0 and it's listed as inactive instead of active.  If I run

mdadm --assemble --scan

it finds md0, sets it up with 1 of the drives and says the other is missing.  It does go active though.

md_d0 stays inactive but loses one of it's disks (the one that goes to md0).

Why does md0 keep being recognized as md_d0 and how can I fix that?

---

### Post by KCormier on 2009-07-11
this thread explains it.

[http://www.linuxquestions.org/questions/linux-software-2/ubuntu-9.04-and-mdadm-721996/](http://www.linuxquestions.org/questions/linux-software-2/ubuntu-9.04-and-mdadm-721996/)

It seems the location of the .conf file is different in 9.04.  As a result your conf changes don't get saved automatically.

needed to run

```

mdadm -Es > /etc/mdadm/mdadm.conf

```

---

