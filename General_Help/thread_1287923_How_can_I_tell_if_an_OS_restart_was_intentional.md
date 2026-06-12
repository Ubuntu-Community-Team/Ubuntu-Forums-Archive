---
title: "How can I tell if an OS restart was intentional?"
date: 2009-10-10
forum: General Help
---

### Post by ShadowTek on 2009-10-10
I might have accidentally clicked on &quot;Restart&quot; instead of &quot;Lock Screen&quot;, or my system just restarted on its own. I would like to be able to know if the shutdown command was actually sent, or if there was some other cause of the restart.  Is there something in the logs that would allow me to tell the difference?

---

### Post by tgalati4 on 2009-10-10
Check the logs in /var/log.

---

### Post by damis648 on 2009-10-10
Or you could just try it again. If it reboots, unintentional.

---

### Post by ShadowTek on 2009-10-10
> Check the logs in /var/log.

Check the logs for what? 
[B]
sudo grep shutdown /var/log/*[/B] doesn't show anything relevant.


> Or you could just try it again. If it reboots, unintentional.

Uhhh, the whole reason that I asked my this question is because I *don't* know what was done.

If it *was* something that happened after I locked the screen, then that would have been the only time that it has done it, so I can't reproduce the effect, as it wouldn't solely be the result of "locking the screen".

---

