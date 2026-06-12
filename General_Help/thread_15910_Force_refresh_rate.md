---
title: "Force refresh rate"
date: 2005-02-17
forum: General Help
---

### Post by Dustie on 2005-02-17
Hi there  :-)

For some reason Xfree wont change away from 60hz and im going crazy looking at all the flicker.

Is there a way to force it to a higher setting?
I've changed the Xfree config file with no luck:

```

Section "Monitor"
	Identifier	"HITACHI CM715"
	HorizSync	31-95
	VertRefresh	50-120
	Option		"DPMS"
EndSection

``` 

Gnome is set on 1280*1024 @ 86hz, but its clearly only at 60hz  ](*,)
I've installed the Nvidia driver for my card (GF 6800), following the guide from ubuntuguide.org.

---

### Post by Dustie on 2005-02-21
Anyone?
I would really like to use Ubuntu, but in 60hz it's not really an option  :?

---

### Post by az on 2005-02-21
CTRL-ALT-F1
login
sudo killall gdm
sudo dpkg-reconfigure -plow xserver-xfree86
take the defaults for what you are presented, except for resolution and refresh rate (you can do advanced, but try to use "medium" first.  You will know what I mean.) 
sudo gdm

---

