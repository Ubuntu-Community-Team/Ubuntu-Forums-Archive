---
title: "Google Earth WIll Not Open"
date: 2011-02-11
forum: General Help
---

### Post by RSASKA on 2011-02-11
Hello,

I just downloaded Google Earth from [http://www.google.com/intl/en/earth/download/ge/agree.html](http://www.google.com/intl/en/earth/download/ge/agree.html), and selected 32-bit deb. 

After it installed, I rebooted the machine.

When I go to Applications > Internet > Google Earth, nothing happens.

I would really like to use Google Earth, please help!

---

### Post by wilee-nilee on 2011-02-11
> **RSASKA said:**
> Hello,

I just downloaded Google Earth from [http://www.google.com/intl/en/earth/download/ge/agree.html](http://www.google.com/intl/en/earth/download/ge/agree.html), and selected 32-bit deb. 

After it installed, I rebooted the machine.

When I go to Applications > Internet > Google Earth, nothing happens.

I would really like to use Google Earth, please help!

Try adding this stuff.
sudo apt-get install lsb-core

---

### Post by dcstar on 2011-02-12
> **wilee-nilee said:**
> Try adding this stuff.
sudo apt-get install lsb-core

All it takes is for Google Earth to have this package listed as a dependency when they create their .deb packages, I find it astounding that they haven't implemented this trivial fix yet!

---

### Post by RSASKA on 2011-05-08
> **dcstar said:**
> All it takes is for Google Earth to have this package listed as a dependency when they create their .deb packages, I find it astounding that they haven't implemented this trivial fix yet!



My system recently crashed and I did a fresh install of Ubuntu

When I get a chance to try this out, will keep you posted.

---

