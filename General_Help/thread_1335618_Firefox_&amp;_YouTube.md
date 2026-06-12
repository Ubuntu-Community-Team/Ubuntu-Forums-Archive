---
title: "Firefox &amp; YouTube"
date: 2009-11-23
forum: General Help
---

### Post by truckbytes on 2009-11-23
I am running Firefox 3.0.15 For some reason I can not play most YouTube videos. Any help would be greatly appreciated.

Thank You
Joel

---

### Post by Native Dialect on 2009-11-23
There have been some issues with the current version of Flash. Here is one possible solution. Uninstall your current Flash plugin with the following terminal command

sudo apt-get remove flashplugin-* --purge

From there, you will install a different Flash plugin, with this command 

sudo apt-get install flashplugin-nonfree

That should square things for you. If not, in the meantime you can download the Midori browser. It will work with the Flash plugin that you get via the synaptic pack manager. Happy browsing.

---

