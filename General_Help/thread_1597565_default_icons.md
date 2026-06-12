---
title: "default icons"
date: 2010-10-15
forum: General Help
---

### Post by saurabhbansal123 on 2010-10-15
i changed the default icons for chrome,thunderbird,synaptic etc. by editing their icons from main menu and clicking on properties... but now the icons dont change with the theme...

i would like to restore my icons so that they change with the theme....

---

### Post by WorMzy on 2010-10-15
Browse to ~/.local/share/applications and look for the respective files (e.g. thunderbird.desktop), once you've found them, either delete them or move them to another folder. Finally, restart gnome-panel by running "pkill gnome-panel".

---

