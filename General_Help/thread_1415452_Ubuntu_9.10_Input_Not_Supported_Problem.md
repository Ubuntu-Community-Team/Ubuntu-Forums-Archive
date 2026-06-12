---
title: "Ubuntu 9.10 Input Not Supported Problem"
date: 2010-02-24
forum: General Help
---

### Post by Aicer50 on 2010-02-24
When i start up Ubuntu 9.10 i get a box saying Input Not Supported, It doesnt go away unless i hit escape and for some reason it automaticly logs me in when i hit esc, even though i have a password set. Here is my xorg.conf My monitor is an Acer AL2017

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

### Post by Aicer50 on 2010-02-24
If i press Logout, the screen works fine, its giving me problems only when im starting up or restarting

---

### Post by Aicer50 on 2010-02-24
Nobody? :(

---

