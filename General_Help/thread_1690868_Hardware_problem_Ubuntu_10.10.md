---
title: "Hardware problem?? Ubuntu 10.10"
date: 2011-02-19
forum: General Help
---

### Post by sir.sargento on 2011-02-19
Hello,

This is a fresh install of Ubuntu 10.10. My hardware seems to be working for the most part. I can play a DVD video in vlc for example. But when I goto Place > Computer it lists CD/DVD Drive and File System. If I right click them and goto Properties it does not give me any information. It says the location is computer:/// for both of them etc...

But if I goto System Monitor > File Systems it shows that it is dev/sda1/ ... I am not sure what is up with this as everything seems to be working except that it will not give me information in properties. Anybody know how to fix this?

Thank you

---

### Post by fabricator4 on 2011-02-19
That's a feature, not a bug.  If you go into computer and list the properties of a device it just gives you basic information, amount of free space etc/

"computer///" is the name of the top level in Nautilus, nothing more.  It has nothing to do with logical device names.

Chris

---

