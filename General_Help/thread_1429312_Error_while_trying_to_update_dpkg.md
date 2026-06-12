---
title: "Error while trying to update dpkg"
date: 2010-03-13
forum: General Help
---

### Post by l3lackEyedAngels on 2010-03-13
Update manager recently tried to provide "Important security updates" for dpkg and dpkg-dev. However, when I click on the 'Install Updates' button, I get the following error:> E: /var/cache/apt/archives/dpkg_1.15.4ubuntu2.1_i386.deb: trying to overwrite '/usr/share/locale/pt_BR', which is also in package apt 0What's going on? Can I ignore this event or should I do something about it?

EDIT: I renamed the pt_BR file to pt_BRx and that appeared to solve the problem. Not sure what started it though.

---

