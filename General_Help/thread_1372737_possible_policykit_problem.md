---
title: "possible policykit problem?"
date: 2010-01-04
forum: General Help
---

### Post by samthurston on 2010-01-04
Within the last week my 9.10 64bit desktop started acting up, here are the symptoms:

[LIST]
[*]desktop effects (compiz) will not load
[*]a windows drive I normally mount manually will not mount (message: Authentication is required)
[*]notification area widget starts empty
[*]sound is off/muted until I manually run gnome audio settings applet
[*]if I try to unlock the users and groups settings dialog it no longer permits me to do so
[*]all these things work from a different account on the same machine
[/LIST]

is there a common thread to these things? it seems like they all might involve policykit in one way or another, but I am unclear on how I would go about fixing these issues, and I'm not finding any good documentation to explain it.

---

### Post by dcstar on 2010-01-05
> **samthurston said:**
> Within the last week my 9.10 64bit desktop started acting up, here are the symptoms:

[LIST]
[*]desktop effects (compiz) will not load
[*]a windows drive I normally mount manually will not mount (message: Authentication is required)
[*]notification area widget starts empty
[*]sound is off/muted until I manually run gnome audio settings applet
[*]if I try to unlock the users and groups settings dialog it no longer permits me to do so
[*]**all these things work from a different account on the same machine**
[/LIST]

is there a common thread to these things? it seems like they all might involve policykit in one way or another, but I am unclear on how I would go about fixing these issues, and I'm not finding any good documentation to explain it.

Something has been changed (or corrupted) in the account with the problems, **exactly** what has been done to change it from the standard setup?

---

### Post by samthurston on 2010-01-05
I fixed the problem, and it was much simpler than I had thought. 

I was going to log out of my session and there it was, my son had changed the session type from "GNOME" to "GNOME Failsafe".

There was nothing else visibly different about my session, so I had no way of knowing I was in failsafe other than that everything was broken. Is this a "feature" I should report?

---

