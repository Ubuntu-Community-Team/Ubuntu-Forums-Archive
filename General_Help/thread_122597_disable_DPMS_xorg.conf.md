---
title: "disable DPMS xorg.conf"
date: 2006-01-28
forum: General Help
---

### Post by jerris86 on 2006-01-28
Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"

this is one section of my xorg.conf file. May i know what must i edit to make sure that DPMS will not be used? 

I keep gettin the problem of my screen blanking out when i start in safe mode.

---

### Post by Jason_25 on 2006-01-28
Just stick a # directly in front of the line like so.

#Option "DPMS"

This is called commenting it out.

---

