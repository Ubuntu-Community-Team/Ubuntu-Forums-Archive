---
title: "Synaptics Package Manager not showing all softwares"
date: 2011-03-23
forum: General Help
---

### Post by xenon91 on 2011-03-23
Generally i install vlc, docky, chromium, eclipse and a bunch of others through Synaptics Package Manager without modifying any settings, but when i installed Ubuntu 10.10 today, the above software show no results in my Synaptics Package Manager. However, some of them were found in Ubuntu Software Manager, but not all.

I checked the repositories and all have been ticked, what else should i be checking?

---

### Post by celldweller1591 on 2011-03-23
well, search them in launchpad.net for PPA. PPA is personnel package archive. They have started migrating some applications to launchpad for PPA install, its a 3 step simple procedure. Only mainstream apps are there in USC or synaptic. Chromioum and eclipse are there in USC.
As of VLC, use this PPA, type the following lines in the terminal 1 by 1 for latest package installation. 
> sudo add-apt-repository ppa:n-muench/vlc
sudo apt-get update
sudo apt-get install vlc

For docky, use these commands - 
> sudo add-apt-repository ppa:docky-core/ppa
sudo apt-get update
sudo apt-get install docky
exit
done.

---

### Post by xenon91 on 2011-03-23
That worked, Thanks.

---

