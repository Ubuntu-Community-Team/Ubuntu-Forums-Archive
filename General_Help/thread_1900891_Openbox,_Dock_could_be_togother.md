---
title: "Openbox, Dock could be togother?"
date: 2011-12-27
forum: General Help
---

### Post by marklennon on 2011-12-27
i would like to use openbox, tint2 and dock to get faster. but it seams that dock(docky, cairo-dock) can't work well in openbox. i have attached two pictures, please check them. and help me if you know how to solve it. 

when i start docky is shows:
[Info 22:14:33.723] Docky version: 2.0.6 Release
[Info 22:14:33.728] Kernel version: 2.6.32.37
[Info 22:14:33.729] CLR version: 2.0.50727.1433

(Docky:28419): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

(Docky:28419): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE

when i start cairo-dock, it shows:
warning : (cairo-dock-opengl.c:cairo_dock_initialize_opengl_backend:171) 
couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...
warning : (cairo-dock-opengl.c:cairo_dock_initialize_opengl_backend:282) 
GLX version too old (1.2).
Cairo-Dock needs at least GLX 1.3. Indirect rendering will be toggled on/off as a workaround.

============================================================================ 
Cairo-Dock version: 2.1.3-10-lucid
Compiled date: Apr 22 2010 01:07:55
Running with OpenGL: 0
============================================================================

warning : (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373) 
while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning : (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:406) 
while trying to load 01empathy.desktop : Key file does not have key 'Is container'
warning : (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:406) 
while trying to load 01f-spot.desktop : Key file does not have key 'Is container'
warning : (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:406) 
while trying to load 01inkscape.desktop : Key file does not have key 'Is container'
warning : (cairo-dock-launcher-factory.c:cairo_dock_load_icon_info_from_desktop_file:406) 
while trying to load 01gcalctool.desktop : Key file does not have key 'Is container'
separateur necessaire
cairo_dock_replace_values_in_conf_file (/home/mark/.config/cairo-dock/current_theme/plug-ins/dnd2share/dnd2share.conf)
warning : (cairo-dock-keyfile-utilities.c:cairo_dock_open_key_file:34) 
No such file or directory
warning : (cairo-dock-keyfile-utilities.c:cairo_dock_open_key_file:34) 
No such file or directory
warning : (applet-load-icons.c:_load_icons:118) 
couldn't detect any drives
cairo_dock_fm_add_monitor_full: assertion `cURI != NULL' failed
warning : (applet-load-icons.c:_load_icons:122) 
Shortcuts : can't monitor drives
warning : (applet-load-icons.c:_load_icons:166) 
Shortcuts : can't monitor bookmarks
separateur necessaire
warning : (applet-dbus.c:_cd_dbus_launch_third_party_applets_in_dir:126) 
Error opening directory '/usr/share/cairo-dock/plug-ins/Dbus/third-party': No such file or directory
warning : (applet-dbus.c:_cd_dbus_launch_third_party_applets_in_dir:126) 
Error opening directory '/home/mark/.config/cairo-dock/third-party': No such file or directory
_cd_shortcuts_update_disk_usage: assertion `myData.pDiskUsageList != NULL' failed
_cd_shortcuts_update_disk_usage: assertion `myData.pDiskUsageList != NULL' failed
_cd_shortcuts_update_disk_usage: assertion `myData.pDiskUsageList != NULL' failed
_cd_shortcuts_update_disk_usage: assertion `myData.pDiskUsageList != NULL' failed
_cd_shortcuts_update_disk_usage: assertion `myData.pDiskUsageList != NULL' failed
_cd_shortcuts_update_disk_usage: assertion `myData.pDiskUsageList != NULL' failed
_cd_shortcuts_update_disk_usage: assertion `myData.pDiskUsageList != NULL' failed
_cd_shortcuts_update_disk_usage: assertion `myData.pDiskUsageList != NULL' failed
_cd_shortcuts_update_disk_usage: assertion `myData.pDiskUsageList != NULL' failed
_cd_shortcuts_update_disk_usage: assertion `myData.pDiskUsageList != NULL' failed

---

### Post by mcduck on 2011-12-27
They should both work just fine, your problem is simply that they both need a compositing manager to be running (for transparency).

Install xcompmgr and add it to your Openbox startup, and the docks should work correctly.

---

### Post by marklennon on 2011-12-27
> **mcduck said:**
> They should both work just fine, your problem is simply that they both need a compositing manager to be running (for transparency).

Install xcompmgr and add it to your Openbox startup, and the docks should work correctly.

thanks, i have installed xcompmgr and solved it.

---

