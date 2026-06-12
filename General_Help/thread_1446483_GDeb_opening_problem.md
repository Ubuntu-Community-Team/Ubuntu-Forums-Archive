---
title: "GDeb opening problem"
date: 2010-04-04
forum: General Help
---

### Post by AmpersUK on 2010-04-04
Hi,

I am trying to load Google's Picasa and keep getting the following:
[INDENT]/tmp/picasa_3.0-current_amd64.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.
[/INDENT]I have looked in Preferences but cannot see what I can do there, can anyone give me a quick fix?

Ampers

---

### Post by Barriehie on 2010-04-04
Preferences > Applications > and for file type extension .deb the program to open would be gdebi-gtk

---

### Post by AmpersUK on 2010-04-04
I have found a quickfix myself, but am a little worried in case I have made an unsafe move - but there's now no urgency as the software has fired up and is working.

I used gksu Nautilus in Terminal and changed the permissions in /tmp to my name and ran gdebi installer from there.

Ampers

---

### Post by AmpersUK on 2010-04-04
I opened the Preferences pull-down menu and there is no item called Applications there.

I went into "Main Menu" to see if Applications was unticked under Preferences there, but again, no mention of Applications at all.

I am using v9.10 Karmic

---

