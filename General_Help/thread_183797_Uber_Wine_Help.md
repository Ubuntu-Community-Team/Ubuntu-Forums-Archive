---
title: "Uber Wine Help"
date: 2006-05-28
forum: General Help
---

### Post by GhandiBurger on 2006-05-28
I think I have messed up wine completely. Could someone show me how to uninstall wine completely and then re-install & configure it correctly? Preferrably in a very n00b friendly way. Thanks

---

### Post by starkes on 2006-05-28
you should be able to go into synaptic and search wine, and then deselect it and hit apply. then repeat the same process again to add it. but through the command line, it would be:

```

sudo apt-get remove wine
sudo apt-get install wine

```

then i think you need to run winecfg...

---

### Post by Sutekh on 2006-05-28
You might also want to remove configuration files.  So use Synaptic to completely remove wine (mark for complete removal)

Or using apt-get
```
 [LEFT]sudo apt-get --purge remove wine
rm -rf ~/.wine
sudo apt-get install wine[/LEFT]

```

---

