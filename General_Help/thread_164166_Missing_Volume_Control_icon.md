---
title: "Missing Volume Control icon"
date: 2006-04-22
forum: General Help
---

### Post by Inwards on 2006-04-22
The volume control icon by the clock and in Totem seems to have gone missing for my main user.  The control is still there: ie; if I click on the space where it used to be I get the master slider, but of course this presents a bit of a usability issue.  I recently added a second user to the system and the control is present for that account.  I'm guessing it's a corrupted icon cache somewhere, but I've been unable to track it down.

Ideas?

---

### Post by SickTwist on 2006-04-22
I think that I have a related problem. I'm running Dapper (all latest updates) with the default Human icon theme and yet one user account has a different icon displayed for the volume applet (see screenshot). I tried purging and re-installing the ubuntu-artwork package but the icon remains. Any ideas?

---

### Post by SickTwist on 2006-04-23
I figured out why the icon is different. Apparently the Tango icon theme contains both SVG and PNG icons that differ visually and the volume applet uses both icons depending on the size of the panel. See [bug #40852]("https://launchpad.net/distros/ubuntu/+source/tango-icon-theme/+bug/40852")

---

### Post by Ramses de Norre on 2006-04-23
~/.icons/theme_name/index.theme
Search [Icon Theme] section
Set line Inherits=theme_name
With theme_name is gnome, or another theme with in his inherits gnome. Inherits are icons which aren't defined by the current theme and you're telling gnome which to use instead. If the inherits of the last theme reffered to are gnome you'll have all common icons set.

---

### Post by Inwards on 2006-04-24
My .icons directory is empty.  Any other ideas?

---

