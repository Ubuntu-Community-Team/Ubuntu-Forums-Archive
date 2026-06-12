---
title: "how can i run a lxterminal --command .desktop link as root"
date: 2010-09-06
forum: General Help
---

### Post by jee_bee on 2010-09-06
I'm tring to make a .desktop link that will let open an applications
with root previlege... i guess than a terminal will have to pop and ask for root pass (that would be perfect for me)

> [ Desktop Entry ]
Version=1.0
Encoding=UTF-8
Name=app nano //EXAMPLE
**Exec=lxterminal [COLOR="Navy"]--command nano [/COLOR]//EXAMPLE**

Exec=lxterminal --command sudo nano
nothing come on...
even whit only: 
Exec=lxterminal --command sudo -s
nothing come on.

please note than i need root previlege for special hardware access*

---

### Post by jee_bee on 2010-09-06
> su-to-root -X -c /&#732;thanks alot to my self...... :rolleyes:

---

