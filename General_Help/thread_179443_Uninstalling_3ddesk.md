---
title: "Uninstalling 3ddesk"
date: 2006-05-19
forum: General Help
---

### Post by minhaz4u on 2006-05-19
Hi ..
Recently I installed a program called 3ddesk...but now it has become an annoyance n want to uninstall it...
Could u please help me out to uninstall tht program
Regards 
Minhas

---

### Post by xXx 0wn3d xXx on 2006-05-19
[QUOTE=minhaz4u]Hi ..
Recently I installed a program called 3ddesk...but now it has become an annoyance n want to uninstall it...
Could u please help me out to uninstall tht program
Regards 
Minhas[/QUOTE]
In terminal (Applications > Accessories > Terminal) type:

> sudo apt-get remove 3ddesktop

And to completly remove it (including all configuration files)

> sudo apt-get remove 3ddesktop --purge

---

### Post by meng on 2006-05-19
Did you install it from repositories? using apt-get or synaptic? If so you can
apt-get remove 3ddesktop

---

