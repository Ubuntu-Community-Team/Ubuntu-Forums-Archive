---
title: "Nautilus causes complete system freeze; Ctrl+Alt+Fx doesn't respond"
date: 2011-05-29
forum: General Help
---

### Post by 3602 on 2011-05-29
During the last several days I have been getting such freezes. It happened maybe three times in five days?

Anyway. All of these freezes happen either while I'm in Nautilus or I'm opening Nautilus. The usual Ctrl+Alt+Fx (x being one to six) to get into the backstage does not work. If I have some music open then it would start looping the last couple of seconds.

Now generally I would go check the logs, but I see no nautilus logs so what should I check?
This is all pretty recent. I *think *that this started to happen when one day exim4 (and some packages all marked exim) got updated but I cannot be certain. Major playing-around after that would be some Wine issues but the system froze once before all that Wine fun.

So step one, what should I check? 

Thank you very much.

EDIT: OK, .xsession-errors ouput:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /home/nietzsche/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/ibus.
gnome-session[1764]: EggSMClient-WARNING: Desktop file '/home/nietzsche/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(polkit-gnome-authentication-agent-1:1840): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1840): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-opengl.c:cairo_dock_initialize_opengl_backend:171) [0m 
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...

 ============================================================================ 
    Cairo-Dock version: 2.3.0~2
    Compiled date:  May 29 2011 11:35:19
    Running with OpenGL: 1
 ============================================================================

[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167) [0m 
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
** Message: applet now removed from the notification area
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-packages.c:cairo_dock_list_packages:699) [0m 
  while listing user packages in '/home/nietzsche/.config/cairo-dock/third-party' : Error opening directory '/home/nietzsche/.config/cairo-dock/third-party': No such file or directory
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-packages.c:cairo_dock_get_url_data_with_post:327) [0m 
  an error occured while downloading 'http://download.tuxfamily.org/glxdock/themes/third-party/2.3.0/list.conf' : Couldn't resolve host name
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-packages.c:cairo_dock_list_net_packages:646) [0m 
  empty packages list on http://download.tuxfamily.org/glxdock/themes (check that your connection is alive, or retry later)
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-packages.c:cairo_dock_list_packages:710) [0m 
  while listing distant packages in 'http://download.tuxfamily.org/glxdock/themes/third-party/2.3.0' : empty packages list on http://download.tuxfamily.org/glxdock/themes
** (nm-applet:1842): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
** (nm-applet:1842): DEBUG: foo_client_state_changed_cb
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension
Unable to open desktop file "wine.desktop for panel launcher

(nautilus:1850): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-2.3.0~2/src/gldit/cairo-dock-packages.c:cairo_dock_get_url_data_with_post:327) [0m 
  an error occured while downloading 'http://xml.weather.com/weather/local/CAXX0385?cc=*&unit=m' : Couldn't connect to server
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
Starting gtk-window-decorator
** (nm-applet:1842): DEBUG: foo_client_state_changed_cb
** Message: applet now embedded in the notification area
I/O warning : failed to load external entity "/home/nietzsche/.compiz/session/10de9d4e97c57bac2130671994555262500000017640040"
/usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
[1;38mwarning : [0m [0;37m(/build/buildd/cairo-dock-plug-ins-2.3.0~2/GMenu/src/applet-util.c:cd_expand_field_codes:120) [0m 
  Unexpected field code %U in exec string 'transmission-gtk %U' : cannot handle file or url codes in the menu.
** (update-notifier:2147): DEBUG: aptdaemon on bus: 0
** (update-notifier:2147): DEBUG: Skipping reboot required
2011-05-29 21:47:06,324 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/view/widgets/mkit_themes.py', 675, 'retrieve')'
2011-05-29 21:47:06,324 - root - WARNING - No styling hints for Shiki-Dust were found... using Human hints.
2011-05-29 21:47:10,961 - softwarecenter.app - INFO - software-center-agent finished with status 1

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
2011-05-29 21:47:18,674 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.6/dbus/proxies.py', 400, '_introspect_error_handler')'
2011-05-29 21:47:18,674 - dbus.proxies - ERROR - Introspect error on :1.44:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.41" (uid=1000 pid=2162 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.44" (uid=0 pid=2189 comm="/usr/bin/python))

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(gnome-power-manager:1826): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
[[1mutils.icon[0m][[1;31mERROR[0m] Icon 'gnome-desktop-config' not present in theme ([1micon.py[0m:49)
[[1mutils.icon[0m][[1;31mERROR[0m] Icon 'folder-home' not present in theme ([1micon.py[0m:49)
/usr/lib/python2.6/dist-packages/ubuntutweak/common/package.py:361: DeprecationWarning: Deprecated, please use 'is_installed' instead
  return self.pkg.isInstalled
/usr/lib/python2.6/dist-packages/ubuntutweak/common/package.py:104: DeprecationWarning: Deprecated, please use 'is_auto_removable' instead
  need_remove = getattr(p, 'isAutoRemovable')
[[1mutils.icon[0m][[1;31mERROR[0m] Icon 'text' not present in theme ([1micon.py[0m:27)
/usr/lib/python2.6/dist-packages/ubuntutweak/common/package.py:127: DeprecationWarning: Deprecated, please use 'is_installed' instead
  if self.cache[pkg].isInstalled and self.is_old_kernel_package(pkg):
/usr/lib/python2.6/dist-packages/ubuntutweak/common/package.py:150: DeprecationWarning: Accessed deprecated property Package.summary, please see the Version class for alternatives.
  return self.cache[pkg].summary

(nautilus:1850): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1850): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(nautilus:1850): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(nautilus:1850): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(nautilus:1850): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(nautilus:1850): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(nautilus:1850): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(nautilus:1850): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GObject'

(nautilus:1850): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(nautilus:1850): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(nautilus:1850): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(nautilus:1850): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(nautilus:1850): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(transmission-gtk:2141): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(transmission-gtk:2141): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(nautilus:1850): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1850): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1850): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
fixme:ole:CoInitializeSecurity (0x452928,-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoInitializeSecurity (0x452928,-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0

(nautilus:1850): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

---

### Post by 3602 on 2011-05-29
I have reinstalled Nautilus thru Synaptic and removed the Samba sharing thing. Let's see how this goes...

---

### Post by shoguevara on 2011-07-29
Did it solve the issue? I have same problem here...

---

### Post by 3602 on 2011-07-29
Well, now I'm using Natty, I really cannot say. Obviously I cannot mark this SOLVED because it ain't, but hey...

---

