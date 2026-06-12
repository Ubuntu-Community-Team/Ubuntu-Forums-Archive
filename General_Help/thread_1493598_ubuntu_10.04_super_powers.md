---
title: "ubuntu 10.04 super powers"
date: 2010-05-26
forum: General Help
---

### Post by johnygeorgemalayil on 2010-05-26
[LIST=1]
[*]   i use ubuntu 10.04.its working quite  normally.i installed ubuntu tweak and compiz fusion etc.For a few days i  didn't have any problem.but after some time in the case of ubuntu  tweak,i am unable to press the 'unlock' button.its as if its freezed or  something.nothing will happen.in the case of compiz fusion i am unable  to change its settings and change the effects.the software center  application which is one of the default applications, i am unable to  install a thing.the install button there is also freezed.like wise i  think my super powers have gone automatically.but when i checked the  users and admin settings i still have the super powers and i am the  administrator.so i deleted that user and made an another user.For a few  days it worked fine.But after some time the same problem became  happening again.What is the solution to it?I think its a bug.
[/LIST]

---

### Post by dino99 on 2010-05-26
maybe you have followed the wrong way to install these packages. 

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

Goto synaptic, select the packages giving troubles, right click on them to remove/purge, when done reselect these packages to reinstall them

---

