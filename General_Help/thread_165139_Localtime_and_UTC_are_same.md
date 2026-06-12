---
title: "Localtime and UTC are same"
date: 2006-04-24
forum: General Help
---

### Post by jimmyj on 2006-04-24
I am having a problem with my clock and I don't know where to look for answers. Everything I've found doesn't help me.

Here is what date gives me, obviously there is something wrong with PDT being the same as UTC.

$ date
Mon Apr 24 23:13:10 America/Los_Angeles 2006
$ date -u
Mon Apr 24 23:14:10 UTC 2006

Running ntpdate pool.ntp.com changes my localtime and UTC over to UTC.

1. The Clock on my bios is set to UTC, /etc/default/rcS reflects this
2. I do not dual boot

Any suggestions would be apreciated.

---

### Post by jeremy on 2006-04-25
if you run kcontrol, then go into 'System Administration' then 'Date & Time' and use 'Administrator mode', you could try changing the setting to manual, or generally play around there...

I am not sure that this will work, but hope to give you a pointer.

---

### Post by aysiu on 2006-04-25
[This thread](http://www.ubuntuforums.org/showthread.php?t=162376) may help.

---

### Post by jimmyj on 2006-04-26
Thanks, that did it. Now my tv listings are spot on.

---

