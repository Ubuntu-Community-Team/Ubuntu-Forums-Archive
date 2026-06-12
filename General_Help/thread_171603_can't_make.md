---
title: "can't make"
date: 2006-05-07
forum: General Help
---

### Post by anubix on 2006-05-07
I've sucessfully got my orinoco driver patched, but when i goto make teh file (as it says in the howto [http://ubuntuforums.org/showthread.php?t=79160](http://ubuntuforums.org/showthread.php?t=79160))
but when i goto make the file, it gives me pages of errors. what can i do?
(and yes i did use sudo)

---

### Post by aysiu on 2006-05-07
Have you installed the *build-essential* package? What are the errors you get?

---

### Post by anubix on 2006-05-07
i have followed all instructions in the how-to, including installing the build essential gcc3.4 like it says. now when i sudo make i get this:
sam@portos:/orinoco/orinoco-0.15rc2$ sudo make
make -C /usr/src/linux-headers-2.6.12-10-386 M=/orinoco/orinoco-0.15rc2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /orinoco/orinoco-0.15rc2/orinoco_pci.o
In file included from /orinoco/orinoco-0.15rc2/orinoco_pci.c:117:
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/orinoco/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/orinoco/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/orinoco/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/orinoco/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/orinoco/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_cor_reset':
/orinoco/orinoco-0.15rc2/orinoco_pci.c:158: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco_pci.c:164: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco_pci.c:171: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco_pci.c:174: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_suspend':
/orinoco/orinoco-0.15rc2/orinoco_pci.c:330: error: too many arguments to function `pci_save_state'
/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_resume':
/orinoco/orinoco-0.15rc2/orinoco_pci.c:347: error: too many arguments to function `pci_restore_state'
make[2]: *** [/orinoco/orinoco-0.15rc2/orinoco_pci.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.15rc2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2

what to do?

---

### Post by aysiu on 2006-05-07
The only other place that error pops up in a Google search is [here](http://ubuntuforums.org/showthread.php?t=19185). I'm not sure if that helps or not.

---

