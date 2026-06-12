---
title: "Eclipse not starting"
date: 2010-01-22
forum: General Help
---

### Post by dvlchd3 on 2010-01-22
Today, eclipse will not start for me.  The initial splash screen comes up, then the attached window pops-up with not text in it...the only way to get rid of the window is to kill the eclipse process from the terminal/command-line.

I have completely purged and reinstalled java and eclipse, but am still having the same issue.  Starting from the terminal also does not give any message besides the "(eclipse:15273): GLib-WARNING **: g_set_prgname() called multiple times" warning. Any ideas or suggestions?

Btw, running Ubuntu 9.10 x86 and the most up-to-date eclipse that is in the repos.

---

### Post by n0dix on 2010-01-22
See this two links: [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/500776](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/500776)
and [http://ubuntuforums.org/showthread.php?t=1362942](http://ubuntuforums.org/showthread.php?t=1362942)

Good luck!

---

### Post by dvlchd3 on 2010-01-22
Unfortunately, downgrading libglib2.0-0 and libglib2.0-data did not fix the issue.  This is particularly annoying as I have a project due soon and need my eclipse  :(

Does anyone else have an information on this issue?  I've been trying to look through bug reports to find something similar, but seem to be coming up short.  I may submit a bug report...however I'm not exactly sure how to recreate, this started happening today...

---

