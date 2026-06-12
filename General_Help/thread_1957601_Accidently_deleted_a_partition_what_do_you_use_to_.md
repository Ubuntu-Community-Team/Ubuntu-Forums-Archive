---
title: "Accidently deleted a partition what do you use to recover yours?"
date: 2012-04-12
forum: General Help
---

### Post by cptrohn on 2012-04-12
I deleted a partition that I need by accident.  It hasn't been overwitten by another OS (I was actually duping a drive)

Any recommendations on anything that can recover it?

---

### Post by oldfred on 2012-04-12
Testdisk would be my first choice. If you  know start & end parted or gparted.


[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")

GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by cptrohn on 2012-04-12
Thanks OldFred.

TestDisk did the trick.... that would have been one freaking expensive mistake.

I owe you a drink.

---

