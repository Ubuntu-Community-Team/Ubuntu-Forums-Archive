---
title: "Cannot install/uninstall Applications"
date: 2009-12-04
forum: General Help
---

### Post by skatinjj on 2009-12-04
I tried to reinstall adobe flash plugin when I installed chromium (at the time I forgot I could just copy the file from the firefox folder to the folder for chromium) and it failed (not sure why it failed I walked away).

Now whenever I try to install/uninstall anything I get this error:

james@ubuntu-desktop:~$ sudo apt-get remove --purge adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

Any suggestions?

---

### Post by Leppie on 2009-12-04
try this:
```
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

---

### Post by skatinjj on 2009-12-04
Thanks, right now it is installing so I will post again when it is done.

---

### Post by skatinjj on 2009-12-04
Thanks again.  This has seemed to fix everything and now I can update =D

---

