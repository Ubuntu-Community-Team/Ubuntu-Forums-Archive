---
title: "using Quantum DAT/DDS/DAT160 drive"
date: 2009-07-31
forum: General Help
---

### Post by e24ohm on 2009-07-31
Folks:
This post really is a continuation of the following thread:
[http://www.ubuntuforums.org/showthread.php?t=1227291]("http://www.ubuntuforums.org/showthread.php?t=1227291")

Is there special commands that I will need to use to get the files compressed to take advantage of the 160 GB compressed capacity?

---

### Post by e24ohm on 2009-07-31
> **e24ohm said:**
> Folks:
This post really is a continuation of the following thread:
[http://www.ubuntuforums.org/showthread.php?t=1227291]("http://www.ubuntuforums.org/showthread.php?t=1227291")

Is there special commands that I will need to use to get the files compressed to take advantage of the 160 GB compressed capacity?

Ok I found the follwoing command

       mt-dds comp-on|comp-off|comp-query|comp-log
       mt-dds < tell|label > [ -b  # ]


How do use these switches to move my .tar and .tgz files on to the tapes, taking advantage of the hardware compression?

---

