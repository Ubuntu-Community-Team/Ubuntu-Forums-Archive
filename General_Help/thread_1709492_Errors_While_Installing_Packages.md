---
title: "Errors While Installing Packages"
date: 2011-03-18
forum: General Help
---

### Post by Grivael on 2011-03-18
While trying to install any package through Synaptic, I receive the following error message:

E: firefox: subprocess installed post-installation script returned error exit status 2
E: firefox-gnome-support: dependency problems - leaving unconfigured
E: openjdk-6-jre-headless: subprocess installed post-installation script returned error exit status 2
E: openjdk-6-jre: dependency problems - leaving unconfigured
E: icedtea-6-jre-cacao: dependency problems - leaving unconfigured
E: icedtea6-plugin: dependency problems - leaving unconfigured
E: chromium-browser: subprocess installed post-installation script returned error exit status 2
E: chromium-browser-l10n: dependency problems - leaving unconfigured

Can anyone help me with this problem? I am booting Ubuntu 10.10.

I also have these same errors when trying to use "sudo apt-get install" in terminal.

---

### Post by andrewthomas on 2011-03-18
```
sudo dpkg --configure -a
```In the terminal

also

```
sudo apt-get install -f
```

---

