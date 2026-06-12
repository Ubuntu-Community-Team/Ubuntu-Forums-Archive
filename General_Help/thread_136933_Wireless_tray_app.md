---
title: "Wireless tray app"
date: 2006-02-27
forum: General Help
---

### Post by DaMasta on 2006-02-27
I'm looking for a wireless signal strength/monitor applet/docklet that resides in the systray. I'd really prefer it not be gnome or kde centric since I run openbox with pypanel. Anyone know of any?

---

### Post by naked on 2006-02-27
[http://gtkwifi.sourceforge.net/]("http://gtkwifi.sourceforge.net/")

This is for Gnome, but might work for you.  I've had the most luck with the application over other wireless apps.

---

### Post by nanotube on 2006-02-27
or try network-manager. its more than just an applet with signal strength - it also automatically connects to any of your wireless profiles and automatically chooses between wired and wireless links.

check out the link in my sig and go to the "multiple wireless profiles" section.

---

### Post by naked on 2006-02-27
GTKwifi also automatically connects you to your prefered network.  I have zero problems moving my laptop between 3-4 AP throughout the day.  However, it doesn't deal with wired networks like nanotube's solution might.

---

### Post by naked on 2006-02-27
Wow. I just install network-manager and nm-applet via Synaptic (0.5.1).  It was completely unresponsive and if I 'killall'ed it, it would respawn twice.  I have 4 of the applet at one time!  I'm sticking with GTKwifi

wifi-radar is another option, but I don't believe that they have an applet/icon.

---

### Post by nanotube on 2006-02-27
hey naked, yea, network-manager is pretty cool. :) i have not tried gtkwifi, maybe its good too. 

but without network-manager, if i have both wifi and wired connected at the same time to the same router (and thus same subnet), net doesnt work at all. (until i manually disable one of them). net-man automagically chooses the best uplink (which is wired, when present).

---

### Post by DaMasta on 2006-02-27
Yeah, I have wifi-radar. And I downloaded gtkwifi and attempted to create a package (I'm using Arch) for it but I couldn't manage. Thanks for the tips.

---

