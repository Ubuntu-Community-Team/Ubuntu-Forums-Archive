---
title: "kubuntu 10.04 upgrade - missing taskbar &amp; black screen"
date: 2010-05-01
forum: General Help
---

### Post by weirdtalk on 2010-05-01
To whom it may help,

When I upgraded kubuntu and restarted I was left without a taskbar and the screen was black. KDE was running (if you hit alt+f2 you got krunner). In the end to fix this I ran this command:
```
sudo apt-get install plasma-desktop
```

Please note this requires internet to do, so if you use wifi it can be a bit tricky. (this was the case for me, I was lucky enough that after setting up the connection in system settings and setting 'auto connect' it connected by itself.)

---

### Post by rvportugal on 2010-05-01
I had the same problem, thanks for the tip!

---

