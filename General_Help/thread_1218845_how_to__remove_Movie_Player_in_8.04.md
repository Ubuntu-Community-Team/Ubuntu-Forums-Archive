---
title: "how to  remove Movie Player in 8.04"
date: 2009-07-21
forum: General Help
---

### Post by pc@rs2006 on 2009-07-21
i typed  sudo apt-get autoremove totemplayer  or sudo apt-get autoremove totem-gstreamer,both failed.:confused:

---

### Post by jerrrys on 2009-07-21
[attach]121860[/attach]

---

### Post by LowSky on 2009-07-21
sudo apt-get remove --purge totem

autoremove command will not remove totem, autoremove is made to uninstall no longer need packages that have no use because you upgraded or uninstalled a related program that doesnt rely on that dependency anymore

---

