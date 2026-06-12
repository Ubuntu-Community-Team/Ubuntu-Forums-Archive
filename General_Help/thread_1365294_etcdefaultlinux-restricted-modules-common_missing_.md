---
title: "/etc/default/linux-restricted-modules-common missing in karmic"
date: 2009-12-27
forum: General Help
---

### Post by go_beep_yourself on 2009-12-27
I need to disable some modules using that file, but it doesn't exist in after Ubuntu 9.04. What can I do?

---

### Post by cariboo on 2009-12-27
Why not just disable the modules you don't want by blacklisting them? Blacklist.conf is located in /etc/modprobe.d

---

