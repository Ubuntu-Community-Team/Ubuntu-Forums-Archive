---
title: "Create Ubuntu Remix OEM"
date: 2009-08-15
forum: General Help
---

### Post by jflarm on 2009-08-15
I am trying to install Ubuntu Remix (UNR) on several netbooks. I know that there was a OEM option for installation where you could finish the install and the owner could create his/her password afterwards.

Anyone knows how to do this with on 9.04 (Jaunty)?

---

### Post by jflarm on 2009-08-16
Bump...

---

### Post by jflarm on 2009-08-20
I found an application called oem-config.

From the command line:

sudo apt-get install oem-config oem-config-gtk

That installs the oem application and a GUI. After the install is made you could use the GUI or issue the command: "oem-config-prepare" . 

The next time the PC is booted the user will be asked to create a new user. The only problem (if you want to call it that way) is that the user created during the install won't be deleted.

---

