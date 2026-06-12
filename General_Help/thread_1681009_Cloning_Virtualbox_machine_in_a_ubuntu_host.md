---
title: "Cloning Virtualbox machine in a ubuntu host"
date: 2011-02-03
forum: General Help
---

### Post by Ceiber Boy on 2011-02-03
I've been trying to clone a virtual machine (in virtualbox), from the terminal:

VBoxManage clonehd [pathe to file] [path to copy location]

VBoxManage showhdinfo [path to cloned disk image]

VBoxManage internalcommand sethduuid [path to clone]

Doing this creates the clone and changes the uuid (Universally Unique Identifier) of the clone to that of the cloned.

This disk can then be attached to Virtual box through creating a new virtual machine and using the clone instead of creating a new disk. This cloned disk will boot but i'm then nagged for Product Activation!

Looking around on google it seams that something has to be done with the .vbox-prev file, as this contains some needed settings?!

That's as far as I've got, can someone please help me finish off this process as i don't want to be nagged by for product reactivation every tine i install the latest release of Ubuntu.

Many thanks

---

### Post by Ceiber Boy on 2011-02-15
this is a crude method but it worked

instsll virtual box on new ubuntu installation, copy '.VirtualBox' amd 'VM Machines' from the home folder of old machine to the home folders of the new machine, open the configuration files in both copied folders and change the user name in the path locations to the new name of your machine, and start VB!

---

