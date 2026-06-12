---
title: "open office help"
date: 2011-07-14
forum: General Help
---

### Post by cowboy7305 on 2011-07-14
The application cannot be started. 
The user interface language cannot be determined.
get this message when i try to open open office  word processor
what is it i can not open any open office in 10.04

---

### Post by dino99 on 2011-07-14
Libreoffice have been chosen by canonical instead of openoffice.
Check that your packages are installed and look at logs

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by cowboy7305 on 2011-07-14
ok but that does not answer my question why is open office now no longer working in ubuntu 10.04

---

### Post by MG&amp;TL on 2011-07-14
I don't know precisely why, but when canonical replace something like an office suite, the ex-suite usually starts to have bugs.

[Canonical ditch open office]("http://www.omgubuntu.co.uk/2011/01/libreoffice-now-default-office-suite-in-ubuntu-11-04/")

---

### Post by grahammechanical on 2011-07-14
If you open the home folder and select view>show hidden files, you will find that there is a folder called .openoffice. It contains the configuration settings related to you using Openoffice. I suggest:

1) You uninstall Openoffice.

2) Rename .openoffice to something else.

3) Re-install Openoffice.

A new .openoffice folder will be created without the configuration conflicts that might be causing this through the files in your present .openoffice folder.

I think that Canonical has only agreed to support Openoffice up to 2012.

By the way when I went from 10.10 to 11.04 Openoffice was removed and Libreoffice was installed and all the settings, such as recent documents list, were migrated into Libreoffice. I had no problems with the change over.

Regards.

---

