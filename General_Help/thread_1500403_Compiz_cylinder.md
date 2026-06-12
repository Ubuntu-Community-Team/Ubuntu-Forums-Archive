---
title: "Compiz cylinder"
date: 2010-06-03
forum: General Help
---

### Post by gemmakaru on 2010-06-03
Any idea how I can get compiz to show a cylinder instead of a cube?  I had a cylinder before the upgrade to lucid but now the option seems to be gone (or moved)?

---

### Post by Klump on 2010-06-03
I'm not sure but you might have to install ```
compiz-fusion-plugins-extra
``` package from the repositories.

---

### Post by blchinezu on 2010-06-03
[B]sudo apt-get install compiz-fusion-plugins-extra compizconfig-settings-manager

[/B] then go to ***menu** > **system**** > **preferences*** > ***compizconfig settings manager***
at the ***effects*** category you'll find ***cube reflection and deformation***
activate it and go to the ***deformation*** _tab_ of that plugin and change the deformation to cylinder or sphere as you like :)

---

### Post by chinmaya_n on 2010-06-03
install **simple-ccsm** from your synaptic....
Using this you can easyly manage those things than in **compizconfig-settings-manager**(ccsm) but **ccsm** is the boss and **simple-ccsm** is just an employee.. :lolflag:
**compiz-fusion-plugins-extra** is must ;)

---

### Post by gemmakaru on 2010-06-03
Absolutely did the trick, thanks.  I guess during the upgrade the old version of the package was removed.  Thanks. :)

---

