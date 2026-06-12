---
title: "No /var/run/lirc/ at startup"
date: 2009-11-28
forum: General Help
---

### Post by jis on 2009-11-28
I installed lirc 0.8.6 (together with ubuntu's lirc) to ubuntu 9.04 and the new version requires /var/run/lirc/ but I find it missing after every reboot. It would have to exist before "/etc/init.d/lirc start" is automatically run. How do you make the directory automatically in conjunction with startup?

---

### Post by cariboo on 2009-11-28
Have you setup lirc to automatically start on boot? More than likely the directory is created when lirc starts and it is removed when lirc shuts down.

---

### Post by jis on 2009-11-29
Lirc is started automatically. Init scripts of Ubuntu's version of lirc are used. I have symlinked newer executables to daemons to replace the use of Ubuntu's binaries.

---

