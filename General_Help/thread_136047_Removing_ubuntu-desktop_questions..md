---
title: "Removing ubuntu-desktop questions."
date: 2006-02-25
forum: General Help
---

### Post by Adrian_b on 2006-02-25
Okay, my plan is to:
Install the full version of Ubuntu, install fluxbox and remove the ubuntu-desktop.
Now, my questions are:
-Will the x-window-system package be uninstalled aswell?
-I presume every application(firefox, totem, ..) will be uninstalled, is there an option to exclude some applications from the install?
-And, when attempting to install fluxconf on my serverinstall yesterday, i failed because of x not being installed(x-window-system-core was installed though), will i have the same problem?

---

### Post by Leif on 2006-02-25
uninstalling ubuntu-desktop will not uninstall any other package (firefox, totem etc.). Meta-packages like ubuntu-desktop pull in programs when you install it, but not when you uninstall. the only possible consideration about uninstalling it is that some changes made between releases depend on it being installed, so your dist-upgrade when dapper comes out may not be as straightforward.

---

### Post by Perfect Storm on 2006-02-25
> -And, when attempting to install fluxconf on my serverinstall yesterday, i failed because of x not being installed(x-window-system-core was installed though), will i have the same problem?

Can't you just install x-window-system-core at the same time?

---

### Post by aysiu on 2006-02-25
Since you say "my plan is," I'm going to assume you haven't already installed the whole ubuntu-desktop at this point.

Your best bet, then, is to do a server install and then do a modification of [a barebones install that Azz advises](http://www.ubuntuforums.org/showpost.php?p=692882&postcount=8): ```
sudo apt-get update
sudo apt-get install x-window-system-core xterm gdm fluxbox menu firefox synaptic
``` **Before** you do that, you'll have to enable the Universe repositories (as that's where fluxbox is). Just do ```
sudo nano /etc/apt/sources.list
``` and remove the # sign from any line that looks like a web address, then save (control-x), confirm (y), and exit (Enter).

---

