---
title: "Urgent: Data recovery from an ext3 partition newly formatted as ext4"
date: 2009-12-15
forum: General Help
---

### Post by Funzo22 on 2009-12-15
Okay guys I just selected my /home drive from the ubuntu installer and chose to use it as an ext4 drive instead of the ext3 that it's formatted to, so of course it automatically checks the box to reformat and me having done the ubuntu installation a billion times and wanting to get through it fast kept pressing next, well needless to say I just lost a lot of years worth of data.


I've been reading this: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) but it's a little outdated and I was wondering if someone can tell me any software they can recommend that ideally will be able to automatically recover as many files as possible, but I am open for any suggestions.


thanks!


Dustin

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
I don't know about software, but I can tell you not to do any read/write operations until you've recovered what you can!

---

### Post by doas777 on 2009-12-15
well, testdisk is the tool you need. you can find it on the [ubuntu-rescue-remix ]("http://ubuntu-rescue-remix.org/Download")bootable cd.
the only problem is that you need another hdd to recover the data to, of greater (or equal) size.
don't do anything with that drive until you are done recovering. every bit you overwrite is one that is harder or impossible to recover.

---

### Post by oldfred on 2009-12-15
I agree on testdisk and links to more info, you can download from the repositories and it is on most recovery disks:

repairs including testdisk info & link to testdisk
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

