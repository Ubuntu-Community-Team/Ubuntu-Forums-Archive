---
title: "moving home to separate partition, room for OS?"
date: 2011-04-30
forum: General Help
---

### Post by sdowney717 on 2011-04-30
going to do this today. 
How much room to leave for the OS?

and any good guides? 
[http://www.hackourlife.com/move-home-to-a-new-partition-ubuntu-10-04/](http://www.hackourlife.com/move-home-to-a-new-partition-ubuntu-10-04/)

---

### Post by JDorfler on 2011-04-30
I've done this for years.  You don't need much for the actual OS if it's a Linux distro.  I've seen folks do it with as little 20Gigs for the / partition leaving everything else for the /home partition minus swap.  Personally I use 50Gigs for my / partition, 50Gigs for my /usr, 20Gigs for /tmp, and use the rest for my /home.  However I recommend having more than one HDD to do this.  However, having your partitions as /, /home, and swap isn't bad at all.  This way when you upgrade your distro in the future you can format your / partition and leave your /home partition alone you can do a clean install without losing your data and some of your settings.  However, make sure you turn all visuals off before upgrading.

---

### Post by Lateralis on 2011-04-30
```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              39G  5.9G   32G  16% /
/dev/sda8              37G   18G   17G  52% /home

```

This is what I have got set for my system.  In hindsight, /home could have been larger and / a bit smaller, but this was my first attempt at something approaching a partitioning scheme.  I also don't have *that* much installed, as I mostly use this laptop for work stuff.  But, there's some idea for you.

---

