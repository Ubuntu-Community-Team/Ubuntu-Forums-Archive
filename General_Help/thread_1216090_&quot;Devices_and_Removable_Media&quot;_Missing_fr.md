---
title: "&quot;Devices and Removable Media&quot; Missing from Preferences Menu"
date: 2009-07-17
forum: General Help
---

### Post by lightnb on 2009-07-17
Hi everyone,

There used to be an option on the Preference menu called "Devices and Removable Media" or something similar, where you could specify auto-play actions for when CDs are inserted, etc.

I can't seem to find it on the menu any more, and it's not an option in the menu editor (right click, Edit Menus) either. Does anyone know the actual command so I can add it again?

Thanks!

---

### Post by merlinus on 2009-07-17
usr/lib/thunar-volman/thunar-volman-settings

I use thunar as my file manager, and installed it and the volume manager via synaptic.

---

### Post by lightnb on 2009-07-17
I'm thinking the command I'm looking for would start with "gnome-".

Like

```
gnome-default-applications-properties
```

or

```
gnome-network-preferences
```

I have a feeling it's already installed, just not on the menu.

---

### Post by lightnb on 2009-07-18
Ok, I got the dialogue by using:

```
aptitude install gnome-volume-manager
```

...but the "Devices" tab is missing! It only has "Cameras", "PDAs", Printers & Scanners, and "Input Devices".

I need to remove the autoplay action for CD insertion.

---

