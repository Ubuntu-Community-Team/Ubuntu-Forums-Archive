---
title: "Ubuntu stuck at boot animation"
date: 2010-08-23
forum: General Help
---

### Post by ThePowerOutage on 2010-08-23
I installed Ubuntu 10.4 Lucid through WUBI last week and havn't had anything wrong with it until today, when I booted up and everything ran normally until the Ubuntu splash. It just loads forever. I let it run over night and it didn't get anywhere. XP boots fine. I don't realy wont to re-install as then I would have to reinstall all my programs, and I would lose the Android SDK and all my progress so far. Thanks In Advance.

---

### Post by amauk on 2010-08-23
At the grub menu (press & hold shift during boot to display menu)
take out "quiet splash" from the kernel boot options
this will disable the splash screen, and give you more verbose output, and hopefully the exact cause of the problem will be apparent

---

### Post by ThePowerOutage on 2010-08-24
When I removed quiet splash it booted as in safety mode. The only error is something to do with my grafix card and that's been there since day one, and hasn't presented any problems. It boots to a similar place as before, except instead of the pretty GUI there's just a flashing underscore in the top left corner. Nothing else happens after that.

P.S. Before it went down I'd been trying to increase my swap bit it came up that the swap.disk was busy. Could this have anything to do with it?

---

### Post by ThePowerOutage on 2010-08-26
Bump

---

