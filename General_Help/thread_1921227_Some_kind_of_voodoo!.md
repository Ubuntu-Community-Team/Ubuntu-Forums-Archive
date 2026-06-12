---
title: "Some kind of voodoo!"
date: 2012-02-06
forum: General Help
---

### Post by spiraloid on 2012-02-06
So my installation of Ubuntu was having some issues and I wanted to put it on another partition, so I did a clean reinstall. First I saved my packages list from synaptic, then I backed up my home folder into a tar.bz2 and stored that away on a separate drive and began the reinstall process. I booted up my ubuntu 11.10 lili usb key, went into gparted and wiped out the old partition, and set up a new one on another disk. I launched the Ubuntu installer, told it to format the new partition and installed.

Once booted up into the brand-spanking-new system, I added back all the PPAs and other 3rd party software sources I had been using, imported the saved package list and hit go. Some time later the installation of 1070 packages had finished so I restarted and logged in.. except something caught me by surprise: it appears my desktop settings from my previous installation had come back. Window theme settings (I had moved my window buttons to the right), desktop settings such as what icons to show on the desktop and even their locations, font settings, unity launcher settings including what applications I had set to stay there, etc. But, I had not yet extracted the backup of my home folder, nor had I turned on Ubuntu One.. I didn't have much time to really get into it, but at a glance it would appear as though my gconf database had somehow restored itself and perhaps more from out of the ether.

FWIW I had placed the backup of my home folder in a file of the same time (except with .tar.bz2) in /home as preparation to extract it, I just hadn't gotten to that yet. Could it possibly have looked in there? Where did these settings come from?

---

### Post by Frogs Hair on 2012-02-06
Some configuration folders reside in home/hidden folders . If they were included in the backup the folders and configurations would be transfered to the new installation .

---

### Post by spiraloid on 2012-02-06
> **Frogs Hair said:**
> Some configuration folders reside in home/hidden folders . If they were included in the backup the folders and configurations would be transfered to the new installation .

Except I wiped that all out. I deleted the old partition and created/formatted a new one for the new installation on a different physical disk... I don't have a /home partition, it's all just on one partition mounted at /.

I am well aware of dotfiles and dotfolders and they would be in the .tar.bz2 as I fully intend to copy them back into my home folder but as I mentioned, I have not yet extracted it. That would've been next, following the reboot after reinstalling all the packages from my saved package list.. but this voodoo happened before I got to that point.

I'm really very confused about this. Albeit somewhat delighted because it saves me the time of merging my backed up settings.. but I could see where this sort of thing might be an annoyance. I just wish I could figure out how it happened.

---

