---
title: "dead laptop screen"
date: 2012-09-03
forum: General Help
---

### Post by sp176 on 2012-09-03
I have had my laptop screen fail.  I wish to use a secondary monitor via HDMI, but it is always booting up to an extended screen.  I know how to set this up as the primary screen, but I am blind to all of my menus, because they load on the laptop screen that is dead.

Any one know a work around?

Luckily I backed up all my data, but my computer is still good except for the screen.

---

### Post by HermanAB on 2012-09-03
Hmm, I've been in that situation.  It is similar to doing long distance server management, so you could try running sshd and then using ssh -X to connect to localhost from a terminal on the secondary screen (or from a completely separate machine) and then launch any utility you need using that somewhat roundabout way.

---

### Post by dcstar on 2012-09-03
> **sp176 said:**
> I have had my laptop screen fail.  I wish to use a secondary monitor via HDMI, but it is always booting up to an extended screen.  I know how to set this up as the primary screen, but I am blind to all of my menus, because they load on the laptop screen that is dead.

Any one know a work around?

Luckily I backed up all my data, but my computer is still good except for the screen.

Plug in an external keyboard and mouse, close the laptop screen to force it to only use the external.

If you know what you are doing you can probably edit the /etc/X11/xorg.conf file to only use the external monitor.

---

