---
title: "remove an old ubuntu &amp; resize the partition"
date: 2009-11-05
forum: General Help
---

### Post by hughcrowther on 2009-11-05
I recently tried to upgrade to 9.10 but it messed up and failed start at all leaving me with a dead computer. I got a friend to get me a copy of 9.10 to install but that has now partitoned off 11gbits leaving 65gbit unusable in the old ubuntu partition 
How can I wipe the 65g and extend its space to my new 9.10?

---

### Post by Zoot7 on 2009-11-05
Gparted is the tool you want. To install it
```
sudo apt-get install gparted
```

That'll let you partition your hard driver appropriately. It's quite easy use, resizing or moving partitions is a snap with it. Alternatively, if you can't boot Ubuntu, you can grab a gparted livecd here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by hughcrowther on 2009-11-05
Thanks that has done the trick!!!):

---

### Post by Zoot7 on 2009-11-05
> **hughcrowther said:**
> Thanks that has done the trick!!!):
You're welcome. Glad to hear you're sorted now. :)

---

