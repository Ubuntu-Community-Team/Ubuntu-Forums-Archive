---
title: "Show full path in Nautilus?"
date: 2012-09-15
forum: General Help
---

### Post by ChaosChris2009 on 2012-09-15
Using Nautilus 3.4.2

Is there any way way I can make it show the full path?

I've looked around in the settings but found nothing. 

Pinguy OS 12.04

---

### Post by Epodx64 on 2012-09-15
just go to "GO"-->Location

or

just hit ctrl+L

---

### Post by ajgreeny on 2012-09-15
> **ChaosChris2009 said:**
> Using Nautilus 3.4.2

Is there any way way I can make it show the full path?

I've looked around in the settings but found nothing. 

Pinguy OS 12.04
If you want it only sometimes, just use Ctrl+L and the breadcruimbs will disappear and full location will take its place.

If you want it to be the default Install dconf-tools, run dconf-editor, and navigate to **org-gnome-nautilus-preferences** and select the "always-use-location-entry".

---

