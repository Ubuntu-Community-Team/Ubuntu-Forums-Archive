---
title: "purging software from the system"
date: 2012-01-05
forum: General Help
---

### Post by seminal on 2012-01-05
Hi,
What's the real way to purge software from my machine?  When I uninstall things via the software center GUI and then run sudo apt-get purge foo, and then run a search I still see build scripts and huge, wasteful PNG files of the 'purged' program.

Thanks

---

### Post by spacecheck on 2012-01-05
> **seminal said:**
> Hi,
What's the real way to purge software from my machine?  When I uninstall things via the software center GUI and then run sudo apt-get purge foo, and then run a search I still see build scripts and huge, wasteful PNG files of the 'purged' program.

Thanks

How about running ```
sudo apt-get clean
```

Good Luck!

---

### Post by bluexrider on 2012-01-05
Ubuntu-Tweak comes to mind or use BleachBit. 

They can help clean your files

---

