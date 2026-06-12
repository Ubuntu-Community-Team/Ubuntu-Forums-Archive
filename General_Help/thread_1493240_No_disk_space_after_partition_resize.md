---
title: "No disk space after partition resize"
date: 2010-05-25
forum: General Help
---

### Post by brentb37043 on 2010-05-25
Hey Guys,
I am new to Linux and I need some help. I just increased the size of my Linux partition using gparted, but it still shows to be almost full. When I look at the disk usage analyzer, it shows that the partition size increase worked. If I right click the home folder and select properties, it shows up as 128TB file size. The partition is only 66GB.

Thanks for your help.

---

### Post by brentb37043 on 2010-05-25
I don't know why I didn't check gparted's website first. I found the answer there. If you have this problem, boot from the live cd again, select partition, select check. Gparted will check the partition for errors and try to fix them. It worked for me.

---

