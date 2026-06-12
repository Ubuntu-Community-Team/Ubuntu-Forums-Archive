---
title: "Upgrade 10.10 fail. Black screen Gnome."
date: 2010-11-02
forum: General Help
---

### Post by kirkface8 on 2010-11-02
Yesterday I attempt to use update-manager to do a distribution update.
all was going good. i went to the kitchen to get a coffee and returned to a black screen with no cursor. the install couldnot have finished as it was still downloading updates i believe.

on reboot gnome did not respond so my last resort was to use kde for the time being. by running update-manager through kde I successfully updated to ubuntu 10.10. After completion of the update i restarted and gnome still had a non respinsive black screen on login. 

Kde is still working fine.

How can I fix this?
Or at least how can I completely reinstall gnome.

Thanks

---

### Post by kirkface8 on 2010-11-02
solved 
by entering 
```

sudo apt-get install --reinstall ubuntu-desktop

```

solved this by obviously reinstalling gnome.

---

