---
title: "Please help me drag a launcher into Cairo"
date: 2010-01-27
forum: General Help
---

### Post by schwabdale on 2010-01-27
Please help me drag a launcher into Cairo. It is not working. I had it working before.

Thanks

---

### Post by hhlp on 2010-01-27
we need more information, execute cairo in terminal and paste here what you get

---

### Post by schwabdale on 2010-01-27
warning :  (cairo-dock-draw-opengl.c:cairo_dock_get_opengl_config:1693)  
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  this module ('/usr/lib/cairo-dock/libcd-Dbus.so') needs at least Cairo-Dock v2.1.0, but Cairo-Dock is in v2.0.9-karmic1
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:376)  
  this module ('/usr/lib/cairo-dock/libcd-switcher.so') needs at least Cairo-Dock v2.1.0, but Cairo-Dock is in v2.0.9-karmic1
  It will be ignored
gtk_widget_get_gl_context: assertion `GTK_IS_WIDGET (widget)' failed
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:182)  
  Key file does not have key 'scroll speed'
warning :  (cairo-dock-config.c:cairo_dock_get_double_key_value:182)  
  Key file does not have key 'scroll accel'
cairo_dock_replace_values_in_conf_file (/home/dj/.config/cairo-dock/current_theme/plug-ins/rendering/rendering.conf)
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
 wget "http://themes.cairo-dock.org/dustbin/Metal/Metal.tar.gz" -O "/tmp/cairo-dock-net-file.sApE9u" -t 2 -T 5
--2010-01-27 13:59:07--  [http://themes.cairo-dock.org/dustbin/Metal/Metal.tar.gz](http://themes.cairo-dock.org/dustbin/Metal/Metal.tar.gz)
Resolving themes.cairo-dock.org... failed: Name or service not known.
wget: unable to resolve host address `themes.cairo-dock.org'
warning :  (cairo-dock-themes-manager.c:cairo_dock_download_file:282)  
  an error occured while executing ' wget "http://themes.cairo-dock.org/dustbin/Metal/Metal.tar.gz" -O "/tmp/cairo-dock-net-file.sApE9u" -t 2 -T 5'
warning :  (cairo-dock-themes-manager.c:cairo_dock_get_theme_path:1121)  
  couldn't retrieve distant theme Metal : couldn't get distant file Metal/Metal.tar.gz
 ====> cThemePath : (null)
cairo_dock_create_surface_from_image_simple: assertion `cImageFile != NULL' failed
cairo_dock_create_surface_from_image_simple: assertion `cImageFile != NULL' failed
gtk_widget_set: assertion `GTK_IS_WIDGET (widget)' failed
iNbConfigDialogs <- 1
warning :  (applet-init.c:_load_theme:90)  
  dustbin : couldn't find images, check the existence of te files in (null)
warning :  (applet-trashes-manager.c:cd_dustbin_count_trashes:232)  
  Attention : Error opening directory '/home/dj/.local/share/Trash/files': No such file or directory
Binding '<Control>F1' failed!
warning :  (cairo-dock-keybinder.c:cd_keybinder_bind:303)  
  couldnt bind <Control>F1
Binding '<Control>F2' failed!
warning :  (cairo-dock-keybinder.c:cd_keybinder_bind:303)  
  couldnt bind <Control>F2
cairo_dock_refresh_launcher_gui ()

VERIFIER LE CHANGEMENT DE CONTAINER POUR TERMINAL

sh: emerald: not found
warning :  (applet-trashes-manager.c:cd_dustbin_measure_directory:257)  
  Attention : Error opening directory '/home/dj/.local/share/Trash/files': No such file or directory
iNbConfigDialogs <- 0

---

### Post by fabounet on 2010-01-28
I would just recommend to install it from the official repository, and not the Ubuntu one.

---

### Post by finlost on 2010-01-31
Either the official repository doesn't exist or it is down.

---

### Post by fabounet on 2010-01-31
it's on launchpad.net for the moment.

---

