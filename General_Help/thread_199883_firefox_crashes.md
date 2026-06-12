---
title: "firefox crashes"
date: 2006-06-19
forum: General Help
---

### Post by guine on 2006-06-19
For the most part firefox has been working just fine since I upgraded to dapper, but on a couple of sites firefox crashes everytime that I click a link on that site.  Anyone have any clues what causing this or how to fix it?  Thanks.

---

### Post by aysiu on 2006-06-19
You can try [this](http://ubuntuforums.org/showthread.php?t=103930).

---

### Post by guine on 2006-06-21
I gave that a try and firefox is still crashing quite often.  I also tried a reinstall through synaptic but that had no effect.  Does a reinstall have to same effect as completely removing all of the files that could possibly be corrupted in firefox from my computer or should completely removing firefox from my computer and then reinstalling it be my next step and if so, what are the files that Id need to make sure that I got rid of?  Thanks.

---

### Post by Rui Pais on 2006-06-21
Hi,
to really clean all files do:
```
sudo apt-get remove --purge firefox
```
take note of anything that is listed to be removed to reinstall after.

Under synaptic theres an option for 'Mark for Complete Removal' instead of simple 'Mark for Removal'.

Have you tried [swiftfox]("http://www.getswiftfox.com")? Its an optimized firefox thats faster then plain firefox and may not gives you that problem. It use firefox existente firefox profile, so you don't loose neither preferences nor expention or themes.

---

