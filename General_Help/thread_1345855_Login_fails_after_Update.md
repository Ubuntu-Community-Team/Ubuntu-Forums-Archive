---
title: "Login fails after Update"
date: 2009-12-04
forum: General Help
---

### Post by kneewax on 2009-12-04
Does anyone else have a problem after yesterdays Karmic update? I let update-manager do an update that included nautilus componants yesterday.  

Now I have a normal boot until login. After entering Password the OS appears to start. Skype (its one of my startup apps)appears but without any borders or title bar. And nothing more happens, I get no panels, no wallpaper, no desktop or icons etc.  But the machine doesn't 'hang' as I can use skype and the mouse remains active - alt-F2 however doesn't work.

Please any ideas? Thanks

---

### Post by efflandt on 2009-12-04
**Alt-F2** only works to get to 2nd console if you are already in a console.  From X you also need Ctrl key, like **Ctrl-Alt-F2**.  From there Alt-Fn where n < 6, are various consoles.  Alt-F7 would take you back to X.  Alt-F8 (or Ctrl-Alt-F8 from X) is sometimes logging console.

Maybe something you installed uses older kernel headers.  I had that problem after I tried to enable an nVidia driver that apparently used older kernel headers than the updated kernel just installed that session in Qimo for kids (based on Xubuntu 8.10) on an old laptop.  I got X back when checked **sudo less /var/log/apt/term.log**, found that dkms was that nVidia package that relied on older kernel headers, did **sudo apt-get purge dkms**. then rebooted.  Maybe it was not accelerated, but at least it worked with default drivers.

---

### Post by khelben1979 on 2009-12-04
If the system is running out of disk space you might get problems. I wonder how it looks like over there. Run
```
df -h
```
from a console and paste your output here.

---

