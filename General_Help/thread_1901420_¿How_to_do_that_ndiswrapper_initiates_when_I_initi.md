---
title: "¿How to do that ndiswrapper initiates when I initiate session in Lubuntu 11.10?"
date: 2011-12-28
forum: General Help
---

### Post by jmsm_1987 on 2011-12-28
¿How to do that ndiswrapper initiates when I initiate session in Lubuntu 11.10?

I have ndiswrapper installed in Lubuntu 11.10. I want that ndiswrapper initiates automatically when I initiate session. I do not know how to create the modified script necessary to achieve it.help please

---

### Post by Unkn0wn1 on 2012-01-05
Enter the following commands into a shell, to write to the modules file

sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi

then, make a link in the /etc/modprobe.d folder, with the name of ndiswrapper.conf, to /etc/modules.conf

Same for any distro :)

---

