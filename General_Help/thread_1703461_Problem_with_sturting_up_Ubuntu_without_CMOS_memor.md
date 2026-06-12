---
title: "Problem with sturting up Ubuntu without CMOS memory battery."
date: 2011-03-09
forum: General Help
---

### Post by rexio on 2011-03-09
Hi,

I'm new to this forum and due to problem where to create this thread, I'm making it here.

I have unusual problem. In my computer with Ubuntu 9.10 the battery backing CMOS memory is dead (and replacing it is not an option).  This requires from me to set up RTC time in BIOS each time I turn on computer (default date is from couple years back). When I don't set time, Ubuntu don't want to startup and it shows me fallowing message :

[I]/dev/sdb1 : Superblock last mount time (Tue .... 2011, now = Mon ...2008) is in the future.

/dev/sdb1 : UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
 
mountall: fsck / [842] terminated with status 4
mountall: Filesystem has errors: /
init: mount main process (840) terminated with status 3
Mount of filesystem faild.
A maintenance shell will now be started.[/I]


So here is my question : Is there any way to run Ubuntu without having RTC time set over, and over again in BIOS ? (It's acceptable for me not to have current time).

---

### Post by wiggly81 on 2011-03-09
why cant you just replace the battery, and why are you so sure it is the battery if you have not replaced it... also bios runs before anything else so I would assume there is nothing you could do with Ubuntu to solve this.

---

### Post by sanderj on 2011-03-09
Have you googled for it? http://www.google.nl/search?q="Superblock+last+mount+time"+"is+in+the+future" gives some inspiration, for example [http://forums.debian.net/viewtopic.php?f=10&t=45797](http://forums.debian.net/viewtopic.php?f=10&t=45797)

---

