---
title: "Why Rhythmbox repeatedly trying to install?"
date: 2010-06-25
forum: General Help
---

### Post by rizameister on 2010-06-25
Why is Rhythmbox (just like other default applications  aka totem ... which i don't need since i have alternatives) repeatedly trying to install through update?
And why update wants to remove FrostWire?
How to avoid that?
[IMG]http://img293.imageshack.us/img293/8948/update.png[/IMG]

---

### Post by dcstar on 2010-06-26
> **rizameister said:**
> Why is Rhythmbox (just like other default applications  aka totem ... which i don't need since i have alternatives) repeatedly trying to install through update?
And why update wants to remove FrostWire?
How to avoid that?


Probably because the system is trying to upgrade the ubuntu-desktop meta-package, and these are included in that package.

Let the upgrade run, then reinstall frostwire.

---

### Post by rizameister on 2010-06-26
> **dcstar said:**
> Probably because the system is trying to upgrade the ubuntu-desktop meta-package, and these are included in that package.

Let the upgrade run, then reinstall frostwire.

I was dependency problem with frostwire. Firstly I have forced to install frostwire via terminal because i have had java bot not the required version, then i got right version, and that solved it. System is not trying to update anymore.

---

