---
title: "a big black sreen"
date: 2006-02-02
forum: General Help
---

### Post by peter 25 on 2006-02-02
hi i am runing ubuntu 5.10 on and x86 when i start it up my sreen goes to my dual boot when ubuntu start up i can see it loading  then when my password screen  comes to apper my screen goes black and goes to sleep
i installed my nvdia drivers with  AUTOMATIX how cani fix my srew up? in safe mode!

---

### Post by dcstar on 2006-02-02
[QUOTE=peter 25]hi i am runing ubuntu 5.10 on and x86 when i start it up my sreen goes to my dual boot when ubuntu start up i can see it loading  then when my password screen  comes to apper my screen goes black and goes to sleep
i installed my nvdia drivers with  AUTOMATIX how cani fix my srew up? in safe mode![/QUOTE]
CTRL-ALT-F1 and you should get a text login screen, log in and then:

sudo dpkg-reconfigure xserver-xorg

then sudo reboot and see if things are better.

If it is still no good, repeat and select the VESA video driver to get you basic functionality.

---

