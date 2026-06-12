---
title: "cairo-dock crashing"
date: 2012-02-15
forum: General Help
---

### Post by subehsharma on 2012-02-15
I see these messages even though the keys are not 'binded' anywhere:

warning : (/build/buildd/cairo-dock-2.4.0~2/src/gldit/cairo-dock-dock-manager.c:get_config:1400)
no shortcut defined to make the dock appear, we'll keep it above. Binding '<Control>F6' failed! warning : (/build/buildd/cairo-dock-2.4.0~2/src/gldit/cairo-dock-keybinder.c:cd_keybinder_bind:311)
Couldn't bind <Control>F6 This shortkey is probably already used by another applet or another application _cd_find_volume_name_from_drive_name: assertionpDrive != NULL' failed Binding 'F1' failed! warning : (/build/buildd/cairo-dock-2.4.0~2/src/gldit/cairo-dock-keybinder.c:cd_keybinder_bind:311)
Couldn't bind F1 This shortkey is probably already used by another applet or another application Binding 'F2' failed! warning : (/build/buildd/cairo-dock-2.4.0~2/src/gldit/cairo-dock-keybinder.c:cd_keybinder_bind:311)
Couldn't bind F2 This shortkey is probably already used by another applet or another application cairo_dock_create_surface_from_image_simple: assertion cImageFile != NULL' failed Binding '<Control>F10' failed! warning : (/build/buildd/cairo-dock-2.4.0~2/src/gldit/cairo-dock-keybinder.c:cd_keybinder_bind:311)
Couldn't bind <Control>F10 This shortkey is probably already used by another applet or another application _cairo_dock_create_surface_from_desktop_bg: assertioniRootPixmapID != 0' failed warning : (/build/buildd/cairo-dock-plug-ins-2.4.0~2.1/switcher/src/applet-load-icons.c:cd_switcher_load_desktop_bg_map_surface:196)
couldn't get the wallpaper warning : (/build/buildd/cairo-dock-2.4.0~2/src/cairo-dock.c:_cairo_dock_intercept_signal:167)
Cairo-Dock has crashed (sig 8). It will be restarted now.`

---

### Post by subehsharma on 2012-02-16
anybody?

---

### Post by Ms. Daisy on 2012-02-16
You may check these sources for solutions:

[http://www.glx-dock.org/](http://www.glx-dock.org/)

[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by subehsharma on 2012-02-16
Thanks but the links don't discuss the problem I'm having.

---

### Post by raja.genupula on 2012-02-16
> **subehsharma said:**
> I see these messages even though the keys are not 'binded' anywhere:

warning : (/build/buildd/cairo-dock-2.4.0~2/src/gldit/cairo-dock-dock-manager.c:get_config:1400)
no shortcut defined to make the dock appear, we'll keep it above. Binding '<Control>F6' failed! warning : (/build/buildd/cairo-dock-2.4.0~2/src/gldit/cairo-dock-keybinder.c:cd_keybinder_bind:311)
Couldn't bind <Control>F6 This shortkey is probably already used by another applet or another application _cd_find_volume_name_from_drive_name: assertionpDrive != NULL' failed Binding 'F1' failed! warning : (/build/buildd/cairo-dock-2.4.0~2/src/gldit/cairo-dock-keybinder.c:cd_keybinder_bind:311)
Couldn't bind F1 This shortkey is probably already used by another applet or another application Binding 'F2' failed! warning : (/build/buildd/cairo-dock-2.4.0~2/src/gldit/cairo-dock-keybinder.c:cd_keybinder_bind:311)
Couldn't bind F2 This shortkey is probably already used by another applet or another application cairo_dock_create_surface_from_image_simple: assertion cImageFile != NULL' failed Binding '<Control>F10' failed! warning : (/build/buildd/cairo-dock-2.4.0~2/src/gldit/cairo-dock-keybinder.c:cd_keybinder_bind:311)
Couldn't bind <Control>F10 This shortkey is probably already used by another applet or another application _cairo_dock_create_surface_from_desktop_bg: assertioniRootPixmapID != 0' failed warning : (/build/buildd/cairo-dock-plug-ins-2.4.0~2.1/switcher/src/applet-load-icons.c:cd_switcher_load_desktop_bg_map_surface:196)
couldn't get the wallpaper warning : (/build/buildd/cairo-dock-2.4.0~2/src/cairo-dock.c:_cairo_dock_intercept_signal:167)
Cairo-Dock has crashed (sig 8). It will be restarted now.`

try with reinstalling .

---

### Post by subehsharma on 2012-02-16
Done that already. Still the same issue.

---

### Post by raja.genupula on 2012-02-16
I think we need purging ...just try this 
```

sudo apt-get remove --purge cairo-dock
sudo apt-get install cairo-dock 
```

let us know what you got . 
All the best .

---

