---
title: "Problem with libreoffice extension"
date: 2011-06-04
forum: General Help
---

### Post by magodiafano on 2011-06-04
Hello I wanna install pdf import extension on libreoffice. But I have a problem:
[http://extensions.services.openoffice.org/en/project/pdfimport](http://extensions.services.openoffice.org/en/project/pdfimport)

In this website I downloaded the linux version and when I tried to install the extension I get this message

[IMG]http://img695.imageshack.us/img695/6493/screenshotxhs.png[/IMG]

What's the error?

---

### Post by linuxinstalledfromhdd on 2011-06-04
Did you install all of your plugins for libreoffice yet?

[http://cinderbox.net/2011/03/29/libreoffice-ubuntu-ppa-makes-installation-easy/](http://cinderbox.net/2011/03/29/libreoffice-ubuntu-ppa-makes-installation-easy/)

---

### Post by magodiafano on 2011-06-04
> **linuxinstalledfromhdd said:**
> Did you install all of your plugins for libreoffice yet?

[http://cinderbox.net/2011/03/29/libreoffice-ubuntu-ppa-makes-installation-easy/](http://cinderbox.net/2011/03/29/libreoffice-ubuntu-ppa-makes-installation-easy/)

no... it's libreoffice I found on ubuntu. What do I have to do?

---

### Post by linuxinstalledfromhdd on 2011-06-04
Did you install the PPA and do:

sudo apt-get upgrade

If it still doesn't work, completely uninstall it with synaptic package manager.

Clean out the configuration files with something like Ubuntu-Tweak..

And then reinstall it from the guide I posted above.

---

### Post by magodiafano on 2011-06-04
> **linuxinstalledfromhdd said:**
> Did you install the PPA and do:

sudo apt-get upgrade


sorry I am a n00b! do I have to write simply this command in the terminal? Or do I have to go in a directory or something similar?

---

### Post by linuxinstalledfromhdd on 2011-06-04
Let's assume you have the application installed incorrectly.

Open terminal and run:

sudo synaptic

Then search for libreoffice and right click on it and select completely uninstall it.

Then return to this guide and follow the instructions:

[http://cinderbox.net/2011/03/29/libreoffice-ubuntu-ppa-makes-installation-easy/](http://cinderbox.net/2011/03/29/libreoffice-ubuntu-ppa-makes-installation-easy/)

---

### Post by pksadiq on 2011-06-04
did you try :
```
sudo apt-get install libreoffice-pdfimport
```
  you may install this from the Software Center

---

