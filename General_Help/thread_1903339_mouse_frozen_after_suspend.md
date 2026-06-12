---
title: "mouse frozen after suspend"
date: 2012-01-02
forum: General Help
---

### Post by kurja on 2012-01-02
Suspending the computer and waking up after used to work fine, but after changing settings in cgonf-editor - apps - gnome power management - lock (I unticked suspend and hibernate so that I wouldn't need to enter a password when waking up the computer) now the mouse is dead when the computer wakes from suspend.

Help?

---

### Post by kurja on 2012-01-02
current situation - just woke up from suspend and the mouse *does* work, but the pointer has become invisible. Very convenient, I'm telling you. Any ideas on how to fix this?

---

### Post by kurja on 2012-01-02
logging out and back in brings back the cursor. hmm.

---

### Post by shakabra on 2012-01-02
Depending on the computer and mouse type I would guess you have a EHCI module suspend problem. If you could post your pm suspend logs we could know for sure.

---

### Post by kurja on 2012-01-02
here's from the log.

---

### Post by kurja on 2012-01-02
bumpety bump, anything?

---

### Post by kurja on 2012-01-03
update: the mouse becomes visible again whenever entering or leaving the  login screen; if I suspend from the login screen it's invisible until  I've logged back in, but if I suspend from the desktop "power button"  and after resuming choose either log off or switch user, then the mouse  caret will be visible in the login screen.

Google finds bug reports of this, but they're from 2010 and I would expect those exact issues to have been fixed by now?

I can't see anything obviously wrong in that log file. Can you help with this?

---

### Post by kurja on 2012-01-06
I reset the settings that I changed prior to getting this problem, but the mouse issue persists. This is very inconvenient. Can you offer any advice?

---

### Post by kurja on 2012-02-26
This issue hasn't been solved, any ideas, anyone?

---

