---
title: "[HELP] xsession-erros in Ubuntu 9.10"
date: 2009-11-07
forum: General Help
---

### Post by bach on 2009-11-07
I am running Ubuntu Linux 9.10 on a DELL notebook. I upgraded to the current version from version 9.04. (I did not do a fresh install.) I see several errors in the file .xsession-errors and I suspect that the long delay I get after I enter my login and password until I see the Gnome desktop has to do with them. See the contents of .xsession-errors below. 

Can anyone help me fix these errors? Thank you. 

CONTENTS OF .xsession-errors


/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

(gnome-settings-daemon:1885): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:1885): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Starting gtk-window-decorator
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!

(polkit-gnome-authentication-agent-1:1979): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1979): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
I/O warning : failed to load external entity "/home/cribari/.compiz/session/109d622b1610baab00125763611910899000000018060038"
Starting Dropbox...
(nautilus:1966): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:1960): DEBUG: Adding applet 0.
** (gnome-panel:1960): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:1960): DEBUG: Adding applet 1.
** (gnome-panel:1960): DEBUG: Adding applet 2.
** (gnome-panel:1960): DEBUG: Adding applet 3.
** (gnome-panel:1960): DEBUG: Adding applet 4.
Initializing nautilus-gdu extension
** (gnome-panel:1960): DEBUG: Adding applet 5.
** (gnome-panel:1960): DEBUG: Adding applet 6.
** (gnome-panel:1960): DEBUG: Adding applet 7.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
** (gnome-panel:1960): DEBUG: Adding applet 8.
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
** (gnome-panel:1960): DEBUG: Adding applet 9.
** (gnome-panel:1960): DEBUG: Adding applet 10.
** (gnome-panel:1960): DEBUG: Adding applet 11.
** (gnome-panel:1960): DEBUG: Adding applet 12.
** (gnome-panel:1960): DEBUG: Adding applet 13.
** (gnome-panel:1960): DEBUG: Adding applet 14.
** (gnome-panel:1960): DEBUG: Adding applet 15.
** (gnome-panel:1960): DEBUG: Adding applet 16.
** (gnome-panel:1960): DEBUG: Adding applet 17.
** (gnome-panel:1960): DEBUG: Adding applet 18.
** (gnome-panel:1960): DEBUG: Adding applet 19.
** (gnome-panel:1960): DEBUG: Adding applet 20.
** (gnome-panel:1960): DEBUG: Adding applet 21.
** (gnome-panel:1960): DEBUG: Adding applet 22.
** (gnome-panel:1960): DEBUG: Adding applet 23.
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
** (gnome-panel:1960): DEBUG: Adding applet 24.
** (gnome-panel:1960): DEBUG: Adding applet 25.
** (gnome-panel:1960): DEBUG: Adding applet 26.
** (gnome-panel:1960): DEBUG: Adding applet 27.

(gnome-panel:1960): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 21
Done!
** (gnome-panel:1960): DEBUG: Adding applet 28.
** (gnome-panel:1960): DEBUG: Adding applet 29.
Initializing nautilus-dropbox 0.6.1

** (nautilus:1966): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1966): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1966): WARNING **: No marshaller for signature of signal 'ShareCreateError'

** (nm-applet:1986): WARNING **: Tried to set deprecated property gsm/band

** (nm-applet:1986): WARNING **: Tried to set deprecated property gsm/band

** (nm-applet:1986): WARNING **: Tried to set deprecated property gsm/band

** (nm-applet:1986): WARNING **: Tried to set deprecated property gsm/band

** (nm-applet:1986): WARNING **: Tried to set deprecated property gsm/band
** (nm-applet:1986): DEBUG: foo_client_state_changed_cb
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (gnome-panel:1960): DEBUG: Adding applet 30.
** (gnome-panel:1960): DEBUG: Adding applet 31.
** (gnome-panel:1960): DEBUG: Adding applet 32.
** (gnome-panel:1960): DEBUG: Adding applet 33.
** (nm-applet:1986): DEBUG: old state indicates that this was not a disconnect 9
** (nm-applet:1986): DEBUG: foo_client_state_changed_cb
** (nm-applet:1986): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:1986): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:1986): DEBUG: foo_client_state_changed_cb
** (nm-applet:1986): DEBUG: foo_client_state_changed_cb

---

### Post by falconindy on 2009-11-07
You realize that out of that entire mess, only 5 lines are errors, right? However, you could reduce a lot of that garbage by using Wicd as your network manager.

---

### Post by bach on 2009-11-07
OK, thanks. Any hints as to correct those errors? Thanks again.

---

### Post by darkshado on 2009-11-09
Hello!
Same problem! I think karmic is still full of bugs!

> (gnome-settings-daemon:1831): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Unable to find a synaptics device.
present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 

(polkit-gnome-authentication-agent-1:1942): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1942): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (gnome-panel:1936): DEBUG: Adding applet 0.
** (gnome-panel:1936): DEBUG: Initialized Panel Applet Signaler.

(nautilus:1937): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:1936): DEBUG: Adding applet 1.
** (gnome-panel:1936): DEBUG: Adding applet 2.
** (gnome-panel:1936): DEBUG: Adding applet 3.
** (gnome-panel:1936): DEBUG: Adding applet 4.
** (gnome-panel:1936): DEBUG: Adding applet 5.

(gnome-panel:1936): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -4 and height 24
Starting gtk-window-decorator
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
** (gnome-panel:1936): DEBUG: Adding applet 6.

** (nautilus:1937): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1937): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1937): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
I/O warning : failed to load external entity "/home/myname/.compiz/session/10aba8a2a75070a745125775764957942300000017280025"
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
** (gnome-panel:1936): DEBUG: Adding applet 7.
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

(nautilus:2020): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
evolution-alarm-notify-Message: Setting timeout for 53515 1257811200 1257757685
evolution-alarm-notify-Message:  Tue Nov 10 01:00:00 2009

evolution-alarm-notify-Message:  Mon Nov  9 10:08:05 2009


(nautilus:2082): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:2212): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:2383): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

---

### Post by Yellow Pasque on 2009-11-09
> I think karmic is still full of bugs!
Upstream bugs, yes. I see a lot of the same errors running GNOME on Arch Linux.

---

### Post by darkshado on 2009-11-09
> **Temüjin said:**
> Upstream bugs, yes. I see a lot of the same errors running GNOME on Arch Linux.

Ok, sorry! :) Gnome bugs.

---

