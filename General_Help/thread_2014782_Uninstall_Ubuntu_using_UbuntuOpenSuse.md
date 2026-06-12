---
title: "Uninstall Ubuntu using Ubuntu/OpenSuse"
date: 2012-07-02
forum: General Help
---

### Post by Djabuntu on 2012-07-02
My computer is running Ubuntu 12.04 and the newest OpenSUSE, can't remember exact name. Is it possible to remove Ubuntu using OpenSUSE or using Ubuntu? Or remove OpenSUSE. I don't need two, that's why.

---

### Post by angry_johnnie on 2012-07-02
it is possible.  just keep in mind where the bootloader keeps its files.  if you're using ubuntu's grub, then you can use a live cd to delete the suse partition and resize ubuntu.  then all you'd need to do is run update-grub from your ubuntu installation.

if you're using suse's bootloader and decide to erase it, you' need to either delete ubuntu and update grub from suse, or delete suse, and then re install grub from live cd.

[here]("http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/") is a guide to reinstall grub 2 from live cd.

just keep an eye on the type of partitions you have and where they are located.  you may not only have to resize them.  you may actually have to move them, as well.

backing up any important data would be a good idea.

---

