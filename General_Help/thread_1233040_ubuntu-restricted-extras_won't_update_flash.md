---
title: "ubuntu-restricted-extras won't update flash"
date: 2009-08-06
forum: General Help
---

### Post by peterx14 on 2009-08-06
Hi all,

When I installed Ubuntu 9.04, I installed the Adobe Flash plugin using the ubuntu-restricted-extras package. And all was well.

Right now, I'm running Flash version "10,0,22,87", but it should've been updated to "10,0,32,18".

Synaptic shows the package "adobe-flashplugin" at version 10.0.32.18-1 (which for me is not installed), but it also shows the packages "flashplugin-nonfree" and "flashplugin-installer" both at version 10.0.22.87 (and both show as installed)... so I'm guessing that ubuntu-restricted-extras depends on one of these two packages?

So.... if I now try to install the "adobe-flashplugin" will that cause a problem? And if I try to remove either "flashplugin-nonfree" or "flashplugin-installer" won't that upset anything else I installed when I installed ubuntu-restricted-extras?

(I suspect that one of the pacakages I have installed should've been updated by who ever owns them... but hasn't been?!)

---

### Post by grizzler on 2009-08-06
As far as I know all you need is 'adobe-flashplugin'. You can remove the other two (I did - no problems).

---

### Post by fragos on 2009-08-06
Remove "flashplugin-nonfree" and "flashplugin-installer" and install "adobe-flashplugin".

---

