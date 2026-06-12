---
title: "How do I open gnome-contacts in Oneiric?"
date: 2011-10-10
forum: General Help
---

### Post by chazinams on 2011-10-10
According to Synaptic, I have "gnome-contacts" installed. But when I search for it in the Dash in Oneiric, only Gwibber is found. I also searched System Settings but there is no contact entry.

How do I open this application?

---

### Post by chazinams on 2011-10-11
no one's figured out how to open gnome-contacts?

---

### Post by chazinams on 2011-10-13
bump

---

### Post by crdlb on 2011-10-13
Its .desktop file (/usr/share/applications/gnome-contacts.desktop) contains```
OnlyShowIn=GNOME;
``` which may be preventing it from showing up under Unity. Nautilus, for example, has "GNOME;Unity;"

In gnome-shell, it's in the overview as 'Contacts'.

---

