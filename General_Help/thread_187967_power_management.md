---
title: "power management"
date: 2006-06-03
forum: General Help
---

### Post by alan_daniel on 2006-06-03
Hey, I need to know how to disable all the power management features of Ubuntu (gnome-power-management, acpi, powernowd, apm, everything) because they all cause problems with the old laptop I use.

I need them permanently disabled, and I can't uninstall them because synaptic wants to uninstall the entire ubuntu-desktop with them.

Thanks for the help.

---

### Post by tkjacobsen on 2006-06-03
You can install boot up manager and disable them in there..
```
sudo apt-get install bum
```

after installation it wil be located in system->administration
disable powernowd, apmd, acpi-support and acpid

EDIT: Gnome-power-manager can be disabled for each user in &#347;ystem->preferences->sessions->Startup Programs

---

