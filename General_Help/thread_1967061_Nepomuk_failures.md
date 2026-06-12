---
title: "Nepomuk failures"
date: 2012-04-27
forum: General Help
---

### Post by OldAlgis on 2012-04-27
I noticed that Nepomuk is flaky (at least on my systems). Yesterday I installed kubuntu 12.04 "precise" and updated with some software, this morning I got a failure report on start up:

> The Application KNetAttach has closed unexpectedly.
Apport Version
    2.0.1-0ubuntu 
Architecture
    i386
...
...


The widow that popped up has a tick on the "report problem". Does it mean that the problem has been reported by the system or does it mean that the user (me) should fill a bug report?

---

### Post by leveret on 2012-04-30
I've also experience this since upgrade at the weekend.  I wasn't getting it on the kubuntu 4.8.2 backport under Oneiric.

Irritatingly, Ubuntu's crash popup now replaces the KDE one and doesn't give a backtrace, so I can't even begin to take it upstream.  It did offer to send a crash report - but where to, how can I follow it ?

---

### Post by montuos on 2012-05-01
I too was getting that error since installing Precise, every time I booted, right after a notification that the folder $HOME/.local/share/contacts/ did not exist.

My solution:  I created the missing folder, and did not get either error message when I restarted.

---

### Post by pbhj on 2012-06-02
I already have the .local/share/contacts/ directory but still get the KNetAttach crash on login.

---

