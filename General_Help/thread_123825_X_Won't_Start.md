---
title: "X Won't Start"
date: 2006-01-31
forum: General Help
---

### Post by Drahcir on 2006-01-31
I just installed a fresh copy of Ubuntu 5.10. Everything was working correctly including my X.Org. The first things I did was configure the OS to my liking. One of these things was removing all the programs that I'll never need to use like BitTorrent, GAIM, etc. I didn't remove anything that was related to X.

On my next reboot, I get the text-based login screen. I can start X with the command *startx* without problems, but on the logout screen, it only gives me the logout selection instead of the usually Shut Down, Restart. I have no idea what caused this. How can I get my X working again on startup? Is there a log file anywhere?

Thanks in advance.

---

### Post by morphodone on 2006-01-31
you might have uninstalled gdm

try reinstalling it - 

```
sudo apt-get install gdm
```

---

### Post by Drahcir on 2006-01-31
Thanks it working now. I still pretty sure that I didn't remove it however. It was still displayed in the Services configuration. :-k

---

