---
title: "SSD trim support in lucid? (and a couple other SSD related things)"
date: 2011-06-02
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-02
i was looking at a ssd and it has trim support and says it works on Linux using kernel 2.6.33 and ubuntu 10.04 uses 2.6.32 and i found this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571476](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571476)
since it says fix released under status does that mean lucid (Kernel 2.6.32-32) has trim support?

since we are on the topic of SSDs what is a reasonable size for [FONT=Courier New]/var[/FONT] and [FONT=Courier New]/tmp[/FONT] (i already know how big i need [FONT=Courier New]/home[/FONT]) partitions since it is not a good idea to store them on a SSD since those partition would wear it out faster

also would this be the correct fstab line for a [FONT=Courier New]/tmp[/FONT] ram disk?
```
tmpfs /tmp tmpfs size=500M,nr_inodes=10k,mode=777 0 0
```

---

