---
title: "Problem with services on startup"
date: 2011-04-26
forum: General Help
---

### Post by aety on 2011-04-26
Hey all I just arrived here now, so greatings, i am already a costumer of this forum, but only now i registered myself, so the problem is, that i don't want to open the terminal and say to wampp to start itself, so i made a script and i already put it on init.d folder, and already type the "update-rc.d" command, but unfortunately the service dont start on startup, i need to go to "BUM"(Boot-Up Manager), and tell the service to start...
the service starts, and wampp starts too, but i dont want to worry about that, so i am asking if anyone know whats happening.

script name: wamp_start.sh

```
exec /opt/lampp/lampp start
```

---

### Post by btindie on 2011-04-26
That's not a valid init script. Take a look at the ones in the init.d directory for examples if you want to create one. There may already be one in that stack.

You can also just put that command in /etc/rc.local and have it called from there.

---

### Post by aety on 2011-04-27
Ok thank you

---

