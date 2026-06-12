---
title: "Need help with two very simple things"
date: 2010-02-08
forum: General Help
---

### Post by aviramof on 2010-02-08
i'v finaly managed to install grub 2 properly i used this guide:
[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

i have two problems now:

1.sudo upgrade-from-grub-legacy command at the end of the guide don't work so i can't change it from root to uuid i need a way to update grub other then sudo upgrade-from-grub-legacy because i wasn't actually upgrading from legacy.

2.i need a way to add windows 7 to the menu.

thanks you in advance.

---

### Post by Leppie on 2010-02-08
> **aviramof said:**
> i'v finaly managed to install grub 2 properly i used this guide:
[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

i have two problems now:

1.sudo upgrade-from-grub-legacy command at the end of the guide don't work so i can't change it from root to uuid i need a way to update grub other then sudo upgrade-from-grub-legacy because i wasn't actually upgrading from legacy.

2.i need a way to add windows 7 to the menu.

thanks you in advance.
if you were not upgrading to grub2 from grub legacy, the upgrade-from-grub-legacy will not work...
if you're sure you installed grub2 correctly, what you should do is:
1. run update-grub:
```
sudo update-grub
```
2. run update-grub... :P

---

### Post by aviramof on 2010-02-09
thank you problem solved.

---

### Post by Leppie on 2010-02-09
you're welcome. glad it's working properly now.

use the thread tools to set this issue to solved.

---

