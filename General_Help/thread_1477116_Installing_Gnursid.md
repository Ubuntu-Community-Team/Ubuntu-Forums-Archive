---
title: "Installing Gnursid"
date: 2010-05-08
forum: General Help
---

### Post by rmcellig on 2010-05-08
I am using Art Manager to install some themes on my new 10.04 system. When I try to install some of the themes, the attached message appears. What should I do?

---

### Post by gaaslight on 2010-05-19
some of the old gtk themes don't install window borders properly and will show a "?" overlaid on their name in that tab. these themes won't delete properly either. deleting your ~/.themes folder is the only way to remove them. 

the ~/.theme folder will be regenerated when you log in, using the default themes that came with the distro and whatever you installed using synaptic.

the gnursid theme will install using art manager, but still won't install a window border and therefore won't make the other themes work that require it work properly.

---

