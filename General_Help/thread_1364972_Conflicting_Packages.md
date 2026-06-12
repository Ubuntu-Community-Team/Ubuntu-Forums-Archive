---
title: "Conflicting Packages"
date: 2009-12-26
forum: General Help
---

### Post by RedSingularity on 2009-12-26
I am getting an error about conflicting packages on my  system when i try to install flashplayer.  How can i find what is conflicting?

---

### Post by gradinaruvasile on 2009-12-26
Use the terminal, Luke...

sudo apt-get install flashplugin-installer

---

### Post by RedSingularity on 2009-12-26
Lol, thats what i am doing and i get....................

 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.0.42.34ubuntu0.9.04.1_amd64.deb

---

### Post by gradinaruvasile on 2009-12-26
Hm... You should have begin with this...

What does this tell you:

apt-cache show flashplugin-installer | grep Version:

---

### Post by RedSingularity on 2009-12-26
Version: 10.0.42.34ubuntu0.9.04.1
Version: 10.0.22.87ubuntu2

---

### Post by gradinaruvasile on 2009-12-26
Do you have 64-bit version?

Try this:

sudo dpkg -i /var/cache/apt/archives/flashplugin-installer_10.0.42.34ubuntu0.9.04.1_amd64.deb

what does it say? The same?

---

### Post by gradinaruvasile on 2009-12-26
Also

apt-cache show flashplugin-installer | grep Conflicts:

will tell you what packages are conflicting. Check if any of those is installed.

---

### Post by RedSingularity on 2009-12-26
dpkg: regarding .../flashplugin-installer_10.0.42.34ubuntu0.9.04.1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.0.42.34ubuntu0.9.04.1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.0.42.34ubuntu0.9.04.1_amd64.deb (--install):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.0.42.34ubuntu0.9.04.1_amd64.deb

---

### Post by gradinaruvasile on 2009-12-26
Maybe 

sudo apt-get purge adobe-flashplugin

helps. Then install the other one.

---

