---
title: "How to unload/reload alsa modules during suspend/resume?"
date: 2006-05-14
forum: General Help
---

### Post by dleh on 2006-05-14
If I hibernate my machine via the option on the logout dialog then upon a resume everything works except the soundcard. If I run /etc/init.d/alsa force-reload then it comes back to life, but I would like this to be done automatically.

Any ideas how I can do this? As far as I am aware the machine is using ACPI not APM.

---

