---
title: "Ubuntu 11.04 Randomly Logging Off, May Be Related to VLC?"
date: 2011-07-09
forum: General Help
---

### Post by dangerousnerd on 2011-07-09
Hi all,

Having some trouble with a new install of Ubuntu 11.04.  I use it for work, so I do tend to run quite a few programs at a time.  Namely Pidgin, Firefox, Thunderbird, Chrome, Osmo, LibreOffice Calc, Calculator and Text Editor.  Sometimes I'll listen to music using VLC.

Sometimes (and I can't figure out when), I will be suddenly logged out without warning.  Just BAM, black screen then back to the login screen. Not only does this get annoying, but I've lost work from this happening.

I've had no other problems with the system, so it'd be great if someone can help me figure this out.

My only clue is that it hasn't happened when I was not running VLC, but then again it doesn't happen consistently while running VLC.  Also, it happened today when I wasn't running VLC but was using Calibre (along with my usual programs).

Any ideas?  Maybe I'm doing too much at one time?  Maybe it's the RAM? 

How do I view an error log about what happened?

Thanks in advance!

---

### Post by CatKiller on 2011-07-09
Sounds like X crashing to me. I believe the log for X is at /var/log Xorg.0.log.

---

### Post by dangerousnerd on 2011-07-09
@CatKiller

Thanks for your help!  I looked at the log and couldn't see anything wrong.  I've attached it below if some one wants to take a look.

Edit: DOH! I realized that I was looking at the log from the session.  I took a look at Xorg.0.log.old (and attached it below).  Here's the interesting part:

> Backtrace:
[ 25084.762] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab2b]
[ 25084.762] 1: /usr/bin/X (0x8048000+0x5fad8) [0x80a7ad8]
[ 25084.762] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x3cb40c]
[ 25084.762] 3: /usr/bin/X (_CallCallbacks+0x3e) [0x8074e1e]
[ 25084.762] 4: /usr/bin/X (WriteToClient+0x267) [0x80a7617]
[ 25084.762] 5: /usr/lib/xorg/modules/extensions/libdri2.so (ProcDRI2WaitMSCReply+0x62) [0xa02bf2]
[ 25084.762] 6: /usr/lib/xorg/modules/extensions/libdri2.so (DRI2WaitMSCComplete+0x75) [0xa00fc5]
[ 25084.762] 7: /usr/lib/xorg/modules/drivers/intel_drv.so (0x629000+0x226bc) [0x64b6bc]
[ 25084.762] 8: /usr/lib/xorg/modules/drivers/intel_drv.so (0x629000+0x87d2) [0x6317d2]
[ 25084.762] 9: /lib/i386-linux-gnu/libdrm.so.2 (drmHandleEvent+0xf5) [0x2e8665]
[ 25084.762] 10: /usr/lib/xorg/modules/drivers/intel_drv.so (0x629000+0x7937) [0x630937]
[ 25084.762] 11: /usr/bin/X (WakeupHandler+0x52) [0x8074602]
[ 25084.762] 12: /usr/bin/X (WaitForSomething+0x1ba) [0x80a1f4a]
[ 25084.762] 13: /usr/bin/X (0x8048000+0x27f1e) [0x806ff1e]
[ 25084.762] 14: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[ 25084.762] 15: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0x17de37]
[ 25084.762] 16: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[ 25084.762] Segmentation fault at address 0xb2ca6008
[ 25084.762] 
Caught signal 11 (Segmentation fault). Server aborting
[ 25084.762] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[ 25084.762] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 25084.762] 
[ 25084.784] (II) Power Button: Close
[ 25084.784] (II) UnloadModule: "evdev"
[ 25084.784] (II) Unloading evdev
[ 25084.784] (II) Power Button: Close
[ 25084.784] (II) UnloadModule: "evdev"
[ 25084.784] (II) Unloading evdev
[ 25084.784] (II) Logitech USB Receiver: Close
[ 25084.784] (II) UnloadModule: "evdev"
[ 25084.784] (II) Unloading evdev
[ 25084.785] (II) Logitech USB Receiver: Close
[ 25084.785] (II) UnloadModule: "evdev"
[ 25084.785] (II) Unloading evdev
[ 25084.785] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 25084.849]  ddxSigGiveUp: Closing log

---

### Post by wildmanne39 on 2011-07-09
> **dangerousnerd said:**
> Hi all,

Having some trouble with a new install of Ubuntu 11.04.  I use it for work, so I do tend to run quite a few programs at a time.  Namely Pidgin, Firefox, Thunderbird, Chrome, Osmo, LibreOffice Calc, Calculator and Text Editor.  Sometimes I'll listen to music using VLC.

Sometimes (and I can't figure out when), I will be suddenly logged out without warning.  Just BAM, black screen then back to the login screen. Not only does this get annoying, but I've lost work from this happening.

I've had no other problems with the system, so it'd be great if someone can help me figure this out.

My only clue is that it hasn't happened when I was not running VLC, but then again it doesn't happen consistently while running VLC.  Also, it happened today when I wasn't running VLC but was using Calibre (along with my usual programs).

Any ideas?  Maybe I'm doing too much at one time?  Maybe it's the RAM? 

How do I view an error log about what happened?

Thanks in advance!Hi, also you can click on your home folder and then hit ctrl+h and that will show the hidden files, then scroll to the bottom of the screen and you will see a file with xsession errors look there.

---

### Post by dangerousnerd on 2011-07-09
Here's the xsession-errors_old output attached.

Thanks!

---

### Post by dangerousnerd on 2011-07-16
Alright, it did it again just now.  Nothing was open but the normal programs above.  No VLC, no Banshee, nothing.

Some one please help me!!  I've put the log below:

[INDENT](nautilus:1432): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
** (<unknown>:1423): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1423): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1423): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1423): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (process:1436): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1436): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1423): DEBUG: Connected to proxy

(<unknown>:1423): dee-WARNING **: Transaction from com.canonical.Unity.FilesPlace.SectionsModel is in the past. Ignoring transaction.

(<unknown>:1423): dee-WARNING **: Transaction from com.canonical.Unity.FilesPlace.GroupsModel is in the past. Ignoring transaction.

(<unknown>:1423): dee-WARNING **: Transaction from com.canonical.Unity.FilesPlace.GlobalGroupsModel is in the past. Ignoring transaction.
** (<unknown>:1423): DEBUG: Connected to proxy
** (<unknown>:1423): DEBUG: Connected to proxy

(<unknown>:1423): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1423): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1423): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1423): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1423): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:1423): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
** (<unknown>:1423): DEBUG: MaximizeIfBigEnough: Pidgin window size doesn't fit
** (<unknown>:1423): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
** (<unknown>:1423): DEBUG: MaximizeIfBigEnough: Pidgin window size doesn't fit

(firefox-bin:1972): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
** (<unknown>:1423): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:1972): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
** (<unknown>:1423): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
** (process:1436): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/greg/Dropbox/Work/Invoices/2011DailyTracker.xlsx
** (process:1436): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1423): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
** (process:1436): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(<unknown>:1423): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1423): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1436): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(firefox-bin:1972): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
** (<unknown>:1423): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(<unknown>:1423): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(<unknown>:1423): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (process:1436): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

(firefox-bin:1972): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
** (<unknown>:1423): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
** (process:1436): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1423): DEBUG: MaximizeIfBigEnough: Google-chrome window size doesn't fit

** (<unknown>:1423): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(nautilus:1432): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

(firefox-bin:1972): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
** (<unknown>:1423): DEBUG: MaximizeIfBigEnough: Firefox window size doesn't fit
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
dropbox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
unity-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
autokey-gtk: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
osmo: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
X IO Error
# Document Statistics:
# Document Statistics:
thunderbird-bin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Pidgin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Xlib.protocol.request.QueryExtension
Xlib.protocol.request.QueryExtension
firefox-bin: Fatal IO error 104 (Connection reset by peer) on X server :0.
** (process:1436): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...

** (process:1436): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.[/INDENT]

---

### Post by khentiamentiu on 2011-08-30
I've tracked this through several ubuntu-related forums, looking for a solution, and haven't found one yet. There's nothing in the  X server log, and the xsession errors don't actually tell me what's causing this sudden death syndrome. I hate Unity, but the problem I'm seeing occurs with Gnome. Do I need to go to another distro?

---

