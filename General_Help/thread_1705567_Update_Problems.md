---
title: "Update Problems"
date: 2011-03-12
forum: General Help
---

### Post by 1chess2u Christian on 2011-03-12
I am at a loss as to what is happening with my netbook when it is starting up lately, as after a minute or two after the main splash opens, a message box pops up saying "Not all updates can be installed Run a partial upgrade, to install as many updates as possible.
This can be caused by:
*A previous upgrade which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu"
When I click on the button that says Partial Upgrade and it finishes, it says "Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

compiz
compiz-core
compiz-gnome
compiz-plugins
libcompizconfig0
libdecoration0"
Please help me! I don't know why the Compiz is unauthenticated, because it came from the Software center. I am at a loss.

---

### Post by zvacet on 2011-03-12
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

