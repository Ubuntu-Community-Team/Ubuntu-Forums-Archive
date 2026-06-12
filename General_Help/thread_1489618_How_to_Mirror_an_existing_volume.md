---
title: "How to Mirror an existing volume?"
date: 2010-05-21
forum: General Help
---

### Post by frediE on 2010-05-21
Just wondering if anyone knows how to RAID an existing volume.  lets say i have a 1TB drive with data on it (EXT4).  I purchase another 1TB drive.

How can I mirror the two without data loss?

A side thing to know is it possible to grow that mirror if I replace with larger drives in the future?

Much thanks... I have looked around and haven't found much.  The new Disk Utility in 10.04 is cool (palimpsest) but it doesn't appear to have that ability.

---

### Post by obscurant1st on 2010-05-21
I dont knw much about RAID. But why dont you try dd command if you just want to mirror a volume!

---

### Post by byStanderone on 2010-05-21
...hope this thread helps:[http://ubuntuforums.org/showthread.php?t=135172](http://ubuntuforums.org/showthread.php?t=135172)

---

### Post by frediE on 2010-05-21
excellent suggestions... however i'm looking to do a software mirror between 2 drives.  the first drive already has data on it.

good thing it's not my boot drive.. just a data drive so that should make things easier.

i'm sure it has something to do with mdadm but i'm finding anything that shows how to take an existing data drive and create a software mirror *with* another same size drive.

i'm still looking....  :-)

---

### Post by byStanderone on 2010-05-23
...have you found one?

---

