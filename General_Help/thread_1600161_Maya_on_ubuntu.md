---
title: "Maya on ubuntu"
date: 2010-10-18
forum: General Help
---

### Post by a sandwhich on 2010-10-18
How well would I be able to get Autodesk maya to work on ubuntu? I know that it is made for redhat, but how hard would it be to move to ubuntu?

---

### Post by marin123 on 2010-10-18
red hat is rpm based distro, therefore, its not possible to use it in ubuntu (deb based distro).

[rpm linux]("http://en.wikipedia.org/wiki/List_of_Linux_distributions#RPM-based")

you could install one of rpm based distros and install your app...

---

### Post by gandaran on 2010-10-18
the rpm package can be converted to .deb using alien, google "Autodesk maya ubuntu" theres many articles on how to install it in ubuntu

---

### Post by ragtag on 2010-10-18
For Maya 2008, on Ubunut 9.04, there were some keyboard problems, with keys getting stuck down. I don't know if this is still true in the latest version, but to get around it, you need to do the following:

Open gconf-editor
Set /apps/gnome_settings_daemon/plugins/a11y-keyboard/active to false

Secondly, the text tool in Maya uses some fonts that are not installed by default. You can install them by running:

```
sudo apt-get install t1-xfree86-nonfree
```

As said above, you need to use the alien to convert the rpm's, once that is done, installation should be reasonably straight forward.

---

### Post by stoneage on 2010-10-18
Try these:-

[http://www.ubuntugeek.com/howto-install-maya-matchmover-and-toxic-2011-on-linux-64-bit-ubuntu-10-04.html](http://www.ubuntugeek.com/howto-install-maya-matchmover-and-toxic-2011-on-linux-64-bit-ubuntu-10-04.html)
[http://ubuntuforums.org/showthread.php?t=1555394](http://ubuntuforums.org/showthread.php?t=1555394)

---

