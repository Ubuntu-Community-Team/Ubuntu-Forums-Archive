---
title: "Pulseaudio with &quot;autospawn=no&quot; doesn't start when I log in"
date: 2012-04-30
forum: General Help
---

### Post by J V on 2012-04-30
I set "autospawn=no" in my ".pulse/client.conf" so that I could have more control over my system (And play games that don't play nice with pulseaudio)

However, despite being checked in "Session and startup", pulseaudio doesn't start when I log in any more and has to be started manually.

How do I fix this?

**Edit: **I just hackishly made a dupe in the session and startup list

---

### Post by J V on 2012-04-30
Bump!

---

### Post by J V on 2012-05-16
Bump: I'd rather avoid a hack n slash method such as adding a duplicate entry to the "Session and Startup" section.

Is this a bug? Should I file a bug report?

---

### Post by brainwash on 2012-05-16
I'm getting this error output when I try to run the startup executable manually:
```
$ start-pulseaudio-x11
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
```

---

### Post by J V on 2012-05-16
Yes I get that too from that command but I usually just run "pulseaudio & disown"

---

### Post by brainwash on 2012-05-16
Well, but if there is a problem with *start-pulseaudio-x11*, Pulseaudio won't get started when users log in. This requires further investigation. Actually, getting rid of Pulseaudio would be the best solution. :D

---

