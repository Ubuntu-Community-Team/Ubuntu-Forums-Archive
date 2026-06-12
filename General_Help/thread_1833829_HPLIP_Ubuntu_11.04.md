---
title: "HPLIP Ubuntu 11.04"
date: 2011-08-26
forum: General Help
---

### Post by fleamour on 2011-08-26
I installed HPLIP manually under 10.10 from HPs website.  Anyway after upgrading to 11.04 the print carts would not align.  I assumed this was due to some kinda conflict between installed version & native version, because 11.04 ships with hplip.

I uninstalled my version with:

```
sudo rm -rf /usr/share/hplip
sudo rm -rf /etc/hp

sudo rm -rf ~/.hplip

sudo rm -rf /var/lib/hp
```

As per HPs website.  

I reinstalled both HPLIP & GUI via Ubuntu Software Centre, but when clicking on System> Preferences> HPLIP Toolbox, nothing happens.  So printing is currently on ice.  Anyone know what the hang up is?

---

### Post by fleamour on 2011-08-26
```
hp-toolbox
```

Via terminal returns that it is not installed, however it is...

---

### Post by fleamour on 2011-08-27
Reinstalling over the top with latest HPLIP from HP's website has done the trick...

---

