---
title: "Automatic update hung"
date: 2006-06-15
forum: General Help
---

### Post by greggh on 2006-06-15
I did a new install of Ubuntu and immediately used the update manager to install the 77 updates it said I needed. It got to gnome-terminal-data and just hung there for 15 minutes. I hit some keys to try to kill it and start over. It skipped to the next package, gedit-common, and hung there too. I hit some keys to get out of that as well, and then it started installing the rest of the packages ok. At the end I got the following errors...

E: gnome-terminal-data: subprocess post-installation script killed by signal (Interrupt)
E: gnome-terminal: dependency problems - leaving unconfigured
E: gedit-common: subprocess post-installation script killed by signal (Interrupt)
E: gedit: dependency problems - leaving unconfigured

I rebooted, and update manager siad I was completely up to date. But to be sure, I went into synaptic and manually reinstalled those 4 packages and it went through without an error. Should I be ok now? It seems to be running fine.

---

