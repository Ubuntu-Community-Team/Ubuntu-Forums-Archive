---
title: "access to windows files"
date: 2012-01-27
forum: General Help
---

### Post by shirbal on 2012-01-27
Hello,
i am using ubuntu 11.04 also with windows 7 on the same laptop
how can i get access to my windows files?


thanks
shiran

---

### Post by coffeecat on 2012-01-27
It depends whether you have a wubi installation (Ubuntu installed inside the Windows partition) or a conventional dual-boot with Ubuntu on its own partition.

In either case open a Nautilus file browser. Then...

If wubi - click on "File System" in the left pane. Now open the "host" folder that shows in the main part of the Nautilus window.

If a conventional dual-boot - look for your Windows partition in the list in the left pane. If the partition has a label, you will see that, otherwise it will be listed by size. Click on it, it will be automounted and the contents of your Windows partition will appear in the main part of the Nautilus window.

---

### Post by shirbal on 2012-01-27
its wubi,,
THanks alot!

---

