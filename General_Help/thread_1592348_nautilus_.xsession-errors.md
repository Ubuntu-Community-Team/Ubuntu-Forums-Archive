---
title: "nautilus .xsession-errors"
date: 2010-10-10
forum: General Help
---

### Post by M4570D0N on 2010-10-10
I started seeing this issue with the 10.10rc. After upgrading to the final 10.10 release today I am still getting a recurring error in .xsession-errors with every boot. There is one line that just repeats over and over again indefinitely:

```
(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
```Here's an abbreviated .xsession-errors, with most of the repeating lines excluded:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[1766]: EggSMClient-WARNING: Desktop file '/home/aaron/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
GNOME_KEYRING_CONTROL=/tmp/keyring-FGyzOy
GNOME_KEYRING_CONTROL=/tmp/keyring-FGyzOy

(polkit-gnome-authentication-agent-1:1835): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1835): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
Starting Dropbox...** Message: applet now removed from the notification area
** (nm-applet:1853): DEBUG: old state indicates that this was not a disconnect 0
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.2.0~4/src/gldit/cairo-dock-opengl.c:cairo_dock_initialize_opengl_backend:172) [0m 
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...

 ============================================================================ 
    Cairo-Dock version: 2.2.0-4
    Compiled date:  Oct  7 2010 21:30:10
    Running with OpenGL: 1
 ============================================================================

[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.2.0~4/src/gldit/cairo-dock-modules.c:cairo_dock_load_modules_in_directory:400) [0m 
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
Starting gtk-window-decorator
Done!
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.2.0~4/src/gldit/cairo-dock-packages.c:cairo_dock_list_packages:656) [0m 
  while listing user packages in '/home/aaron/.config/cairo-dock/third-party' : Error opening directory '/home/aaron/.config/cairo-dock/third-party': No such file or directory
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.2.0~4/src/gldit/cairo-dock-packages.c:cairo_dock_get_url_data:287) [0m 
  an error occured while downloading 'http://themes.glx-dock.org/third-party/2.2.0/list.conf' : Couldn't resolve host name
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.2.0~4/src/gldit/cairo-dock-packages.c:cairo_dock_list_net_packages:603) [0m 
  empty packages list on http://themes.glx-dock.org (check that your connection is alive, or retry later)
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.2.0~4/src/gldit/cairo-dock-packages.c:cairo_dock_list_packages:667) [0m 
  while listing distant packages in 'http://themes.glx-dock.org/third-party/2.2.0' : empty packages list on http://themes.glx-dock.org
I/O warning : failed to load external entity "/home/aaron/.compiz/session/10994e4d067957eed7128673360723924500000017660037"
** Message: applet now embedded in the notification area
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.3
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
** Message: Initializing gksu extension...
** Message: nautilus_window_slot_hide_clutter

(nautilus:1831): Gtk-WARNING **: Attempting to add a widget with type FMDesktopIconView to a container of type GtkVBox, but the widget is already inside a container of type GtkVPaned, the GTK+ FAQ at http://library.gnome.org/devel/gtk-faq/stable/ explains how to reparent a widget.
** Message: ALIVE? real_update_query_editor

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nm-applet:1853): Gdk-CRITICAL **: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
/usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

(nautilus:1831): Gtk-WARNING **: Reset to Defaults: missing action Reset to Defaults
** Message: nautilus_window_slot_hide_clutter

(nautilus:1831): Gtk-WARNING **: Attempting to add a widget with type FMIconView to a container of type GtkVBox, but the widget is already inside a container of type GtkVPaned, the GTK+ FAQ at http://library.gnome.org/devel/gtk-faq/stable/ explains how to reparent a widget.

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: nautilus_window_sync_clutter_toogle
** Message: nautilus_window_sync_eterm_toogle

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (update-notifier:2316): DEBUG: aptdaemon on bus: 0
** (update-notifier:2316): DEBUG: Skipping reboot required

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: nautilus_window_sync_clutter_toogle
** Message: nautilus_window_sync_eterm_toogle
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: nautilus_window_sync_clutter_toogle
** Message: nautilus_window_sync_eterm_toogle

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: nautilus_window_sync_clutter_toogle
** Message: nautilus_window_sync_eterm_toogle

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: fm_list_view_clear
** Message: nautilus_window_slot_hide_clutter

(nautilus:1831): Gtk-WARNING **: Attempting to add a widget with type FMListView to a container of type GtkVBox, but the widget is already inside a container of type GtkVPaned, the GTK+ FAQ at http://library.gnome.org/devel/gtk-faq/stable/ explains how to reparent a widget.

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: nautilus_window_sync_clutter_toogle
** Message: nautilus_window_sync_eterm_toogle

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: fm_list_view_clear
** Message: nautilus_window_slot_hide_clutter

(nautilus:1831): Gtk-WARNING **: Attempting to add a widget with type FMIconView to a container of type GtkVBox, but the widget is already inside a container of type GtkVPaned, the GTK+ FAQ at http://library.gnome.org/devel/gtk-faq/stable/ explains how to reparent a widget.

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: nautilus_window_sync_clutter_toogle
** Message: nautilus_window_sync_eterm_toogle
** Message: fm_list_view_clear
** Message: fm_list_view_finalize

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: nautilus_window_sync_clutter_toogle
** Message: nautilus_window_sync_eterm_toogle
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: nautilus_window_sync_clutter_toogle
** Message: nautilus_window_sync_eterm_toogle

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: nautilus_window_sync_clutter_toogle
** Message: nautilus_window_sync_eterm_toogle

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1831): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

```
What's going on here?:confused:

---

### Post by MacUntu on 2010-10-14
This is a bug in ubuntuone-client-gnome. It's actually fixed upstream but with Ubuntu's version you'll get this warning every time you open a folder in nautilus.

It's nothing serious, but if you want to shut it up, you can run:```
gconftool-2 --type bool --set '/apps/ubuntuone/nautilus/show-location' false
```from a terminal.

---

