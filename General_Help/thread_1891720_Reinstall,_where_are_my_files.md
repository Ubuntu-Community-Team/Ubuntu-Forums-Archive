---
title: "Reinstall, where are my files"
date: 2011-12-06
forum: General Help
---

### Post by China Diapers on 2011-12-06
Hey, 

I installed xubuntu over my slackware installation, choosing not to format my home partition when installing xubuntu, presuming my files would still be there when I accessed the home partition from xubuntu. This doesn seem to be the case.

Any ideas? are the hidden somewhere?

---

### Post by zvacet on 2011-12-06
Look with gparted or some similar tool is your partition still on disc or is it deleted.I know,you didn´t format home partition,but just in case.If it is deleted try to save it with **testdisc**.I hope you will not need it but instructions are at [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by aeiah on 2011-12-06
is ubuntu using your parition for home or an area on / ?
```

df -h

```

---

### Post by China Diapers on 2011-12-06
```
/dev/sda1             9.9G  3.3G  6.1G  35% /
udev                  2.0G  4.0K  2.0G   1% /dev
tmpfs                 806M  856K  805M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  2.0G  164K  2.0G   1% /run/shm
/dev/sda6             907G  248M  860G   1% /home
/dev/sdb1             2.0G  772K  2.0G   1% /media/ADRIAN-USB

```

What are these none/run partitions?

---

### Post by China Diapers on 2011-12-06
tmpfs?

---

### Post by Lars Noodén on 2011-12-06
From the look of /dev/sda6, the data seems to be gone.

---

### Post by China Diapers on 2011-12-06
****. Luckily I keep anything important on the cloud these days.

---

