---
title: "Ubuntu Fails to Boot After Hard Shutdown"
date: 2011-04-05
forum: General Help
---

### Post by silverhammermba on 2011-04-05
I was stupidly compiling code on my netbook with 10% battery left. The CPU ate up my battery reeaally quickly and it did a hard shutdown while still compiling.

When I boot up, the Ubuntu loading screen shows up for about two seconds and then it goes to a completely black unresponsive screen. I have a live install on my thumb drive, but I don't actually know what I need to do to fix whatever broke.

**Edit:**
Oo, something happened. When I pressed a key the screen filled up with a bunch of stuff I don't understand. But the last two messages are:

[  450.807328] Fixing recursive fault but reboot is needed!
mountall: Disconnected from Plymouth

What should I do about this?

---

### Post by lithopsian on 2011-04-05
Boot with Live CD and fsck your Ubuntu partitions.  Fingers crossed that will do it.

---

### Post by silverhammermba on 2011-04-05
Thanks, that fixed it!

---

