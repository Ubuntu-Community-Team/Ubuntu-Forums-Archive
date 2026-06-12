---
title: "Remove Gwibber Status Indicator"
date: 2011-03-16
forum: General Help
---

### Post by gofurygo on 2011-03-16
Hello guys

I know this has been discussed in a few threads before, but never exactly addressed my "problem" with the gwibber status indicator.

After a fresh installation of Ubuntu 10.10 I uninstalled empathy (im using skype). The empathy menu in the evolution indicator was gone after that.
I also uninstalled gwibber. But the gwibber status indicator remains within the about-me panel... Uninstalling the gwibber package also removes the me-menu which I want to keep actually. Especially the shutdown/restart... part of it. See attachment
I know there is a shutdown panel-app...but its butt-ugly and it doesnt allow to logon/off. 

In another thread I read that the gwibber status shouldnt be there if no account for it is configured... which it is not... I do use ubuntu-one though which is in the same menu... I saw that this issue was addressed at some bug report before, but not fixed yet...

Does anybody know a good workaround to get rid of the gwibber status in the panel while keeping the about me and the shutdown button?

I dont have gwibber-service running on start-up... just as a side note...

Thanks in advance

---

### Post by gofurygo on 2011-03-17
Anybody got an idea...? :confused:

---

### Post by Krytarik on 2011-03-17
It isn't a dedicated *gwibber status indicator*, instead it is an integral part of the package "indicator-me". If you can relinquish the single "Ubuntu One" menu item, then just purge those package, the indicator-session menu will be preserved then, I have it that way.
```
sudo apt-get purge indicator-me
sudo apt-get autoremove
```
Greetings.

---

### Post by gofurygo on 2011-03-17
Excellent!!! This is exactly what I was looking for. I can spare the Ubuntu-One menu item for getting rid off the gwibber thingy:D

Problem solved, nuff said;)

---

