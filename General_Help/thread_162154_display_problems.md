---
title: "display problems"
date: 2006-04-18
forum: General Help
---

### Post by jakthebomb on 2006-04-18
i have a dell dimetion 2350 with intergraded graphics its a intel 915G
when useing ubuntu 5.10 or any other version the gui is all mesed up.  im trying to find a way to fix it.  it is not a monotor problem it is a driver problem

can anyone help?

---

### Post by Jason_25 on 2006-04-18
Please post your /etc/X11/xorg.conf.  Also, the /var/log/Xorg.0.log will help too.  A quick fix would probably be to change the driver in the xorg.conf from the intel one to vesa.

---

