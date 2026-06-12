---
title: "Garbage in syslog"
date: 2010-01-16
forum: General Help
---

### Post by ccf on 2010-01-16
I've had my laptop crash on my a few times recently, often with little useful information left behind afterwards.  This afternoon, after a crash, the last thing in syslog before the reboot was a bunch of NULs, followed by a chunk of what looked like one of TeX's ls-R files.  I've previously found random bits of XML files (probably from scrollkeeper) in there.  Other than this, there's no useful messages there.

I've not noticed a pattern for the circumstances surrounding it, mainly because they've usually happened while the machine has been unattended.

Any suggestions as to what's happening?

---

### Post by rnerwein on 2010-01-16
hi
don't care about the contents in the file. it just looks like for me that your box paniced and if so you can have anything in any file. look at your directory /var/crash if there is a huge core file.
ciao

---

### Post by ccf on 2010-01-16
Only thing there is a crash in gvfs, which happened *after* the restart, for a problem which has come up before and already been reported (LP 504447).  Is there something in /proc which might be stopping it from dumping?  The lockup happened again about 20 minutes ago - ironically, it dumped syslog.0

---

