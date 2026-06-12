---
title: "Downgrade Possible?"
date: 2009-12-24
forum: General Help
---

### Post by Prominence on 2009-12-24
I upgraded to a newer version of nautilus, and when I found out it didn't work with Gloobus Preview, I wanted to reinstall the patched-nautilus, but I can't, for it says that the installed nautilus is newer therefore not allowing me to install the older patched-gloobus-nautilus, is there a way I can get the Gloobus version back on there?

---

### Post by Ocxic on 2009-12-24
un-install nautlius then install the version you want to install.

---

### Post by lidex on 2009-12-24
There is an option in synaptic to force a version from what is  available in your enabled repositories. Nautilus may prove problematic to downgrade due to inter-dependencies but should be do-able.

I would suggest opening synaptic. Search "nautilus". Mark these packages for uninstallation:
```
nautilus
nautilus-data
libnautilus-extension1
```

Apply. (If it tells you it will have to take out a bunch of packages, you'll have a decision to make.)

Still in synaptic. Individually highlight the packages mentioned, go to "package" menu and select "force version". The box that pops up has a drop-down list of available options. Choose the appropriate version and make sure all three are the same version number. Apply. Reboot.

If you run into difficulties, post back. Make sure you have a recent backup. If you installed this newer nautilus from a third-party repo, I would suggest disabling it.

---

