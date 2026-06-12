---
title: "Toshiba Portege 3500 Tablet PC Screen Rotation"
date: 2006-01-27
forum: General Help
---

### Post by damonkohler on 2006-01-27
Unfortunately, the Option "RandRRotation" "true" trick doesn't seem to work for the Portege 3500. It has a trident video card and not an nvidia one. I haven't been able to find a way to make xrandr work. I get the typical error message about X Error of failed request: BadMatch etc.

Anyone know how to make it work? Or possibly know of a different solution to making the screen rotate?

---

### Post by fargle on 2006-01-31
Well, I'm just getting into Ubuntu - I jumped to Gentoo a couple of years back after the whole Red Hat-Fedora fiasco.  Gotta say, Ubuntu rocks so far!  Gentoo is nice, but MAN does everything just work on Ubuntu, no messing about to get it all configured manually.

Anyway, I have Gentoo on my 3500 right now, (probably not for too long, after some investigation!) and you're right, XRandR is not ready for it yet - I spent quite awhile futzing around trying to get it to work, to no avail.

What I ended up with was using two XF86Configs, one for normal orientation and one for vertical.  Then I use a on-screen button app called Tabatha that lets you execute scripts with button presses using the stylus, and two of the buttons are for portait and landscape.  They just execcute commands that move a symbolic link between the two configs.  You have to log off, and, at least on Gentoo, also tell the X server to restart on logoff so it will re-read the new config.

I also move a link between GDM configs, so that if the screen is in portrait mode, it automatically logs me in without having to try to type in credentials with the stylus.  And there's a little snippet that detects whether the screen is open or closed on startup and chooses the right config - so if I start up with the screen over the keyboard, it automatically detects that, sets up portrait mode, and tells GDM to automatically log me in.  Bit of a security risk, but I figure your average thief is most likely going to start it up like a laptop, at which point it sets landscape and GDM pops up a login prompt.  Sneaky.

Let me know if you need more, and I'll get it hooked back up and copy lots of config files over from it - it's on a private network right now configuring a PIX firewall.

---

### Post by damonkohler on 2006-02-02
Yeah, if I could see those config files, that would be awesome! Thanks!

---

### Post by Lupine on 2006-02-03
Yes please!!! :mrgreen:

---

### Post by dare2dreamer on 2006-04-15
I just got one of these from a friend, so I'd love to see the config files you created for tabatha as well.

---

