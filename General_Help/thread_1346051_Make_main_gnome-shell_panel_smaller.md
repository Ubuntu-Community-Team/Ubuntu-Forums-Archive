---
title: "Make main gnome-shell panel smaller"
date: 2009-12-04
forum: General Help
---

### Post by Soapy.Illusions on 2009-12-04
Quick Question:

How could I make the main panel in gnome-shell (the current version in the karmic repos) smaller, it looks too big on my screen...

And is their a ppa where I can get more recent versions of gnome shell

Thanks,
Soapy

---

### Post by aftermarketgirl on 2010-06-11
It's not configurable via the gui, but gnome-shell is all javascript and css... so if you want to dig into the files, you'll find that option in /usr/share/gnome-shell/js/ui/panel.js

It's 'const PANEL_HEIGHT = 26;'. I knocked mine down to 18, because I agree with you, it doesn't need that much space for what is essentially a clock and a hotspot.

Most of the other visual options (like the font sizes you are going to want to adjust) are in css files in the /usr/share/gnome-shell/theme directory. I had to dig harder to find this one. FYI, any update will fry your new settings.

Link to the ppa I've been using: [https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by ioca100 on 2010-06-13
How can I change the buttons to the left side?
OK, gconf-editor> /desktop/gnome/shell/windows/button_layout>close,minimize,maximize  and close session.

---

