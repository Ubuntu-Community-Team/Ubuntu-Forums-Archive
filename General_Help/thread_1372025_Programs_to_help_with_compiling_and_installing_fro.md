---
title: "Programs to help with compiling and installing from source"
date: 2010-01-04
forum: General Help
---

### Post by cpufreak2589 on 2010-01-04
Sorry if this is the wrong category, it seemed the most relevant.

I am finding that as I play with more and more apps, I am needed to compile and install from source programs that are not available from synaptic. Frequently I have to google for dependencies several times, having to reinstall one and ./configure-ing to see what else I am missing. Is there any sort of script or program I can run that will check for all the dependencies I will need and download (or even download and compile/install) them? Is there a way I can compile a program for my distribution and architecture and submit it for inclusion in synaptic?

---

### Post by drpjkurian on 2010-01-04
If you have any programmes in .deb format, You can install it by using .deb package installer.

For eg Chrome browser,
Addobe flash player etc

---

### Post by DasEi on 2010-01-04
here a link from irc : 

Compiling software from source? Read the tips at [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) 
(But remember to search for pre-built packages first,as said above)


manually add a *deb:

sudo dpkg -I blah.deb

---

### Post by DasEi on 2010-01-04
.

---

### Post by cpufreak2589 on 2010-01-04
> **DasEi said:**
> here a link from irc : 

Compiling software from source? Read the tips at [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) 
(But remember to search for pre-built packages first,as said above)


manually add a *deb:

sudo dpkg -I blah.deb

Hmm, most of that I knew and didn't really help that much, though auto-app seems helpful for some things. Is there a script that will scan the configure file for dependencies, then check my system for them?

I am curious as to how stuff gets made available via synaptic as well. Can I make a .deb and add it to synaptic for everyone?

---

### Post by Vaphell on 2010-01-04
well, you won't get your stuff into the official repos (packages are tightly controlled and thoroughly tested by canonical) but you can set up your own ppa repository that can be added to the source list by the user and then synaptic sees packages located there.

---

