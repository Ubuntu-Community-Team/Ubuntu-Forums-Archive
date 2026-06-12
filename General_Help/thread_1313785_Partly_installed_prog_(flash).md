---
title: "Partly installed prog (flash)"
date: 2009-11-04
forum: General Help
---

### Post by starbase1 on 2009-11-04
Hi All,
This on behalf of a frend I introduced to Ubuntu. (Karmic).

He is having problems with the  Adobe Flash plugin for Firefox, and thinks it may be partly installed - it runs into problems when trying toadd or remove.

Is there a manual method to kill off the old install and try again from a clean start?

Thanks,
Nick

---

### Post by mac9416 on 2009-11-04
Is the package name adobe-flashplugin? Several folks have had trouble with it, and I've been telling them to run these commands, with much success...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Hope that gets it!

---

### Post by starbase1 on 2009-11-04
> **mac9416 said:**
> Is the package name adobe-flashplugin? Several folks have had trouble with it, and I've been telling them to run these commands, with much success...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Hope that gets it!

Thanks for the suggestion, here's hoping that does the trick.

---

### Post by starbase1 on 2009-11-08
yep, works perfectly!

Thanks.

---

