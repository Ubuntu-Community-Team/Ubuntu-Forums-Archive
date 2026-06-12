---
title: "Can't login (10.04)"
date: 2010-04-30
forum: General Help
---

### Post by peril2 on 2010-04-30
Was playing with a script in /etc/init.d, ran upgrade-rc.d then rebooted. Login scree came up, accepted my credentials, blinked then returned to login screen.

Booted from CD and removed the script from init.d and the softlinks from /etc/rc*.d

Still won't let me login. Help!

---

### Post by peril2 on 2010-05-01
D'oh, problem was actually some garbage in .profile. All good now

---

