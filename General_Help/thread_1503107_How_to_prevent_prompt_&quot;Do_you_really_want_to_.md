---
title: "How to prevent prompt &quot;Do you really want to shutdown&quot; ?"
date: 2010-06-06
forum: General Help
---

### Post by pstein on 2010-06-06
When I click "Shutdown" I am always asked for confirmation similar to
 
Do you really want to shutdown
CANCEL SHUTDOWN
 
How can I prevent this annoying prompt and shutdown immediately?
 
I prefer a solution for the good old "Shutdown" menu  and not a comline command.
 
Peter

---

### Post by louieb on 2010-06-06
run gconf-editor

go to aps>indicator-session > check suppress_logout_restart_shutdown

---

### Post by bildr on 2010-06-06
yes, alternately: sudo init 0

---

### Post by jarmore on 2010-06-06
> **louieb said:**
> run gconfg-editor

go to aps>indicator-session > check suppress_logout_restart_shutdown

I tried it ... it wants ```
gconf-editor
``` instead ... but thanks, I wanted to get rid of that again since installing 10.04 :)

---

### Post by gator2802 on 2010-11-04
I tried that and nothing changed.  I am running 10.10 on a dell inspiron 1545.
Thanks

---

