---
title: "RAID 0 - From Centos to Ubuntu"
date: 2012-08-07
forum: General Help
---

### Post by vmicovic on 2012-08-07
Hello,

i have one box which have two RAID 0 (software controller) storage (which is on centos 5.2 x64)
Now i want to switch to ubuntu.
Question is, how to reconnect RAID on new distro?
Is /etc/mdadm.conf only what i need for new distro or not?

Thank you.

---

### Post by vmicovic on 2012-08-08
mmm, nothing.. all pass ok :)
just install mdadm and after restart mount md0, md1, md2 etc...

---

