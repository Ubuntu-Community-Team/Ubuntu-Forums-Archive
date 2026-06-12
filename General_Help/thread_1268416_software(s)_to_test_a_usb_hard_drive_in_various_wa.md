---
title: "software(s) to test a usb hard drive in various ways"
date: 2009-09-16
forum: General Help
---

### Post by pythonscript on 2009-09-16
I just bought a 1 TB Western Digital external hard drive, and I've heard great reviews and terrible reviews on the same coin, so I'm looking to test mine as soon as it comes in. Is there an ubuntu program, hopefully in the repos, that will let me 
a) run a check on every sector of the drive (not the file system, but the actual disk)
and b) write large amounts of data to every sector multiple times. 

I ask about b) so that I can simulate my copying large amounts of actually important documents/photos, etc, to the drive. If it's going to crash, I'd like it to crash *before* it gets out of the six month warranty. Thanks!

---

### Post by earthpigg on 2009-09-16
```
man badblocks
```

:D

also, you could probably write a shell script that will copy a large file over, delete it, and copy it over again over and over again.

---

### Post by pythonscript on 2009-09-16
> **earthpigg said:**
> ```
man badblocks
```:D

also, you could probably write a shell script that will copy a large file over, delete it, and copy it over again over and over again.

I'll check out badblocks; thanks! As for a shell script, how would I guarantee that this hits every sector? If I knew the algorithm for random allocation, I could probably calculate how long, on average, it would take to hit every sector. But... I'm a graduate student in math during the day, so coming home to Linux is my break from all that. :)

---

### Post by earthpigg on 2009-09-16
you can also find the s.m.a.r.t. tools in synaptic.

most modern hard drives contain self-diagnostic firmware.

smart tools talk to that stuff and can tell you what the hard drive has to say about itself.

---

### Post by unutbu on 2009-09-16
bonnie++ is a hard drive benchmarking tool.
Herman has a nice guide on how it is used here:
[http://ubuntuforums.org/showpost.php?p=5743215&postcount=65](http://ubuntuforums.org/showpost.php?p=5743215&postcount=65)

smartmontools is a package which provides the smartctl program.
smartctl can test the health of S.M.A.R.T. (Self-Monitoring, Analysis and 
Reporting Technology System) hard drives. I'm not sure if this works with all USB external drives, but it wouldn't hurt to try it.

caljohnsmith gives instructions for testing hard drive health using smartctl here:
[http://ubuntuforums.org/showpost.php?p=6575111&postcount=32](http://ubuntuforums.org/showpost.php?p=6575111&postcount=32)

---

### Post by 3rdalbum on 2009-09-16
I'm pretty sure there's some disk testing benchmarks available in Phoronix Test Suite ([http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/))

---

