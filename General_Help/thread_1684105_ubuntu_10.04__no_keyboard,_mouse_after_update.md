---
title: "ubuntu 10.04  no keyboard, mouse after update"
date: 2011-02-08
forum: General Help
---

### Post by atl_CCk on 2011-02-08
After an update the system hangs?  No keyboard or mouse ps2.  The screen at F1 had starting up? F7 has graphic login.  Have a 10.10 desktop cd purple in color that I could load to resolve.  Will try to telnet into system.

---

### Post by layolayo on 2011-02-08
Hi, just updated a Toshiba Satellite Pro (model no. rubbed off!) and have this problem also.

recovery mode boots then fails at devmonitor with a TERM signal

booting into Windows partition, keyboard and mouse are fine

have access to the (e)dit and (c)ommand line options but not sure what to do to make necessary adjustments - would seem these are the only places I can make a change to the system.

Any help appreciated!

Just investigating a little further, looks like kernal was been upgraded from -24 to -28 (Lucid), but flunked out during it as the kernal files are there but the grub loader is referencing -24, changing to -28 gives a kernal panic error.

---

### Post by atl_CCk on 2011-02-09
rebooted box and tried recovery?  Looks like it did a lot but no work.  Keyboard worked in recovery?  alt F7 and alt F1 worked?

---

### Post by atl_CCk on 2011-02-09
In maintenance mode.  Is there a fix all statement or command?  The file system is mounted read only?

---

### Post by layolayo on 2011-02-11
Re-installation carried out... not the solution I was after, but it is one that works!

Upgraded OK second time round.

---

