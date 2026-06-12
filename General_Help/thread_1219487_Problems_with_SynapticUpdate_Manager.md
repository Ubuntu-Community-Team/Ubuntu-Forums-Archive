---
title: "Problems with Synaptic/Update Manager"
date: 2009-07-21
forum: General Help
---

### Post by Rawgers on 2009-07-21
To start off, this problem arose after a huge amount of "silly" things that I did. I wanted to upgrade my torrent program "deluge" from 1.1.6 to 1.1.9 but accidently installed the 2.0.0 dev. Since I did not want that, I tried uninstalling Deluge, but I could still open 2.0.0 dev (by typing "deluge" in terminal). I tried many methods of uninstalling (even appeared not installed in "Synaptic Package Manager." So after some "google" research, I found somewhere saying I should manually delete deluge files. I did that, but maybe I did something wrong (deleted something wrong). 

So from there, I went to install Deluge from Package Manager, but I ended up getting an error. Do not entirely remember but it was something on the hand "The program deluge has missing (some word I forgot D:) .please reinstall/uninstall" So not being able to install from Package Manager, Installing by .deb file, or apt-get deluge, I installed it by source with absolutely no problems. But now when openning deluge it just appears blank. But that is not the only/main problem

An error message now appears saying ```
"An error occured, please run Package Manager from the right click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount> 0' This usually means that your installed packages have unmet dependencies.
```

So I openned Package Manager, and a pop up message says "You have 1 broken package on your system!

Use the "Broken" filter to locate it." 
I look at the "broken dependencies" box and deluge package appears (already installed). When I try to reinstall,
```
E: libtorrent-rasterbar2: Package is in a very bad inconsistent state - you should

```
(incomplete message =/)

I also tried to open Update Manager to see if I can update in order to fix the issues. When openning, message saying "Not all updates can be installed"and gives me two options: Partial Upgrade or Cancel.

If I try the Partial Upgrade, an error message appears:```
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later
```

and if I cancel, it says
```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

Here is my log for sudo apt-get install -f
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  deluge-common deluge libboost-thread1.37.0 libtorrent-rasterbar4 deluge-core
  libboost-filesystem1.37.0 libboost-system1.37.0 python-libtorrent
  libboost-python1.37.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  deluge-common deluge-core libboost-filesystem1.37.0 libboost-python1.37.0
  libboost-system1.37.0 libboost-thread1.37.0 libtorrent-rasterbar4
  python-libtorrent
Suggested packages:
  libtorrent-rasterbar-dbg
Recommended packages:
  deluge-console deluge-webui deluge
The following packages will be REMOVED:
  libtorrent-rasterbar2
The following NEW packages will be installed:
  libtorrent-rasterbar4
The following packages will be upgraded:
  deluge-common deluge-core libboost-filesystem1.37.0 libboost-python1.37.0
  libboost-system1.37.0 libboost-thread1.37.0 python-libtorrent
7 upgraded, 1 newly installed, 1 to remove and 1209 not upgraded.
9 not fully installed or removed.
Need to get 0B/4190kB of archives.
After this operation, 7832kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing libtorrent-rasterbar2 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 libtorrent-rasterbar2
```

To conclude, I have absolutely no idea what to do. If I'm missing any information, please tell me.

Thanks for any help~

---

### Post by 3rdalbum on 2009-07-21
```
sudo apt-get install --reinstall libtorrent-rasterbar2
```

---

### Post by Rawgers on 2009-07-22
> **3rdalbum said:**
> ```
sudo apt-get install --reinstall libtorrent-rasterbar2
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python-libtorrent: Depends: libtorrent-rasterbar4 (= 0.14.4-2~jaunty~ppa2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
And apt-get -f install error in my Opening post. =/

---

### Post by Strongman332 on 2009-07-22
have you tried the fix broken packages function of synaptic (i think there is still one)

---

### Post by Rawgers on 2009-07-22
> **Strongman332 said:**
> have you tried the fix broken packages function of synaptic (i think there is still one)

Yea, it did not help =/

---

