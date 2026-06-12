---
title: "how to change refresh rate in GDM"
date: 2011-08-15
forum: General Help
---

### Post by Pro$pect on 2011-08-15
I just did a fresh install of natty on my desktop and at first I had a box bouncing around my screen saying input not supported. I changed my refresh rate from 50 to 52 and it got rid of it, but I still have the bouncing box on the login screen. How can I adjust the refresh rate for that?

---

### Post by Pro$pect on 2011-08-15
is there something I could do like when you change the gdm theme by running this:

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

---

### Post by Pro$pect on 2011-08-15
fixed it, I realized my xorg.conf file was basically empty so I saved over it with a new one from the nvidia settings manager.

---

