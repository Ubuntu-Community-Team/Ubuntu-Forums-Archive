---
title: "How to autostart processes as root?"
date: 2010-05-21
forum: General Help
---

### Post by Muscovy on 2010-05-21
How do I get processes to run as root during startup? I have a random script and a package which both need to run as root in the background, but I can't find a way to do this automatically.

---

### Post by The Cog on 2010-05-21
It was traditionally done by putting the commands in /etc/rc.local. Nowadays you might add a script to /etc/init if you can find good enough documentation about upstart.

---

