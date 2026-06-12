---
title: "Using a CD in 10.10 NBR"
date: 2010-10-04
forum: General Help
---

### Post by tomsimmons on 2010-10-04
Afternoon All

Maybe I'm being stupid here...

If I stick a data CD in the drive it doesn't seem to auto mount, well I'm guessing that's the case because it doesn't appear anywhere in Files & Folders.

Also related to CDs, when I insert a music CD this doesn't start/appear in RhythmBox.

The machine is a eeePC 901 using a USB external drive.



Thanks for any help.


Tom

---

### Post by tomsimmons on 2010-10-04
Using df it would seem that the CD isn't being mounted, which would explain both of these problems...

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              3650632   2589012    876176  75% /
none                    503012       252    502760   1% /dev
none                    508612       120    508492   1% /dev/shm
none                    508612       100    508512   1% /var/run
none                    508612         0    508612   0% /var/lock
none                   3650632   2589012    876176  75% /var/lib/ureadahead/debugfs
```

I would have expected auto mount for CD to be standard?


Tom

---

