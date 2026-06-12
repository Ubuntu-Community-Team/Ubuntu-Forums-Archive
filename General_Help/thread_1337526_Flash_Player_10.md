---
title: "Flash Player 10"
date: 2009-11-25
forum: General Help
---

### Post by tchayden on 2009-11-25
Does any one know which current flash player I should download? it gives me the options of YUM, tar., etc. and how to get them working I can't seem to get them up and running.

---

### Post by wilee-nilee on 2009-11-25
Which distribution are you using.

---

### Post by wojox on 2009-11-25
.deb

---

### Post by wilee-nilee on 2009-11-25
> **wojox said:**
> .deb

Which is provided in Karmic but not beyond Hardy with Adobe direct.

---

### Post by N3X15 on 2009-11-25
> **wojox said:**
> .deb
Hate to break this, but the Flash 10 deb is corrupt AND has additionally screwed up my current install of Flash.  Can't uninstall or reinstall.

---

### Post by emachnic on 2009-11-25
Download the tarball and install via command line. It's easy.

The better option if you don't need the beta is to *sudo apt-get install flashplugin-installer* from the Terminal.

---

### Post by N3X15 on 2009-11-25
> **emachnic said:**
> Download the tarball and install via command line. It's easy.

The better option if you don't need the beta is to *sudo apt-get install flashplugin-installer* from the Terminal.

```

$ sudo apt-get install flashplugin-installer 
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

```

As previously stated, can't uninstall or reinstall.

---

### Post by wilee-nilee on 2009-11-25
> **N3X15 said:**
> Hate to break this, but the Flash 10 deb is corrupt AND has additionally screwed up my current install of Flash.  Can't uninstall or reinstall.

You might just start a thread this is a easy fix, and I doubt the deb is corrupt, but look in synaptic for broken and or missing packages.
Also make sure the medibuntu is loaded.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Soul-Sing on 2009-11-25
> Please try to avoid running more than one update app at a time, e.g. terminal, Synaptic, update-manager GUI and so on.
Close all GUIs and only use terminal.
To avoid this error:
> E:The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it

try these cmds:
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin

sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install -f

sudo apt-get install flashplugin-installer
## Firefox should be closed and all other flash apps (e.g. swfdec, gnash) should be removed.

source: ubuntu-answers

---

### Post by wojox on 2009-11-25
> **N3X15 said:**
> ```

$ sudo apt-get install flashplugin-installer 
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

```

As previously stated, can't uninstall or reinstall.

```

#Remove Flash
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way

```

---

### Post by tchayden on 2009-11-26
Thank you everybody I got it installed and working properly!

---

