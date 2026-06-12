---
title: "Kubuntu startup"
date: 2006-06-05
forum: General Help
---

### Post by sanderjd on 2006-06-05
There are a few things that I would like to start automatically when I log into Kubuntu. On Ubuntu this could be accomplished in the "Sessions" dialog, but I can't seem to find this functionality in KDE. It isn't really worth the trouble of making startup scripts, but if anyone knows a simple way of doing this I would be much obliged. Thanks.

---

### Post by gingermark on 2006-06-05
I think you're going to have to use small startup scripts and place them in your ~/.kde/Autostart directory.

But I've found that KDE remembers your previous session, so if you just don't close the apps you want to startup in your next session then they should start automatically next time (for example, open Kopete, end your session, log back in, and Kopete should automatically start again).

---

### Post by Jucato on 2006-06-05
In the ~/.kde/Autostart directory, you can put links to the things that you want to be executed upon logging into Kubuntu.

Alternatively, in System Settings > KDE Components > Session Manager, you can set it to restore the previous session or manually restore saved session. This will, upon logging in, restore the state of your desktop when you logged out. Meaning whatever programs you left open when you logged out will be reopened when you log back in.

---

