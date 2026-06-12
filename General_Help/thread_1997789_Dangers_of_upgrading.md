---
title: "Dangers of upgrading?"
date: 2012-06-05
forum: General Help
---

### Post by unitedanarchy on 2012-06-05
I want to know if when I upgrade any of my packages will be messed up because I got things for Oneiric.

---

### Post by Varad Vyapari on 2012-06-05
Use the download-only option:

Code:
sudo apt-get update
sudo apt-get --download-only upgrade

u can install the packages later once they are completely downloaded. This should ensure that things aren't messed up!

---

### Post by plucky on 2012-06-05
> **unitedanarchy said:**
> I want to know if when I upgrade any of my packages will be messed up because I got things for Oneiric.

Assuming you mean a distribution upgrade from Oneiric to Precise

If your packages are in the Ubuntu repositories,then they will be upgraded to a newer versions in the Precise repositories.If the packages are from PPAs or third party repositories,they will not be upgraded.

It all depends on what changes you have made to your install,there is no 100% guarantee that everything will work.

It is also worth having a fall back position in case the upgrade doesn't work and you have available a 12.04 install disk or a good backup to re-install your current OS.


Good Luck

---

### Post by unitedanarchy on 2012-06-05
I have a bunch of PPAs in there, And a few games and stuff that are the Oneiric version, Would they still work on 12.04? I also have a fan thing for my mac called macfancontrol or something like that and it was an oneiric script  thing I think.

---

