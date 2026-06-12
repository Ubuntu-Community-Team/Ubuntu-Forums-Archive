---
title: "Grub trouble"
date: 2010-05-28
forum: General Help
---

### Post by LiamG on 2010-05-28
I use an HP Mini 1000 110 with Ubuntu 10.04. I'm not actually sure that the trouble I am having is related to the grub, but I like the phrase "grub trouble".

I recently did a clean install of 10.04. I'm quite happy with it in general but I've been having some issues booting it up. Often, when I switch the machine on, I see the HP flash screen (where I can enter the BIOS) and then get a blinking cursor, which does not move, no matter how long I wait. I kill the power and try again. Sometimes it takes 5 or 6 tries to get it to load. When it loads, everything works fine--I'm writing on the same computer right now. At first I thought that it only did this when waking up from hibernate, but now it seems to happen when I shut down as well. In fact, I think that the problem is happening more frequently. Does this sound familiar to anyone? I'd appreciate any help I can get.

---

### Post by LiamG on 2010-06-01
Does anybody have any advice about this? It's becoming a bit of a pain.

---

### Post by dino99 on 2010-06-01
many users around there have this kind of bad issues, you have to watch your logs to know what is wrong on your system:

- .xsession-errors in /home (unhide it with menu)
- system admin log viewer

check that your video driver is well activated: system admin hardware driver

---

### Post by LiamG on 2010-06-01
There do seem to be some questionable things going on in the xsessions-errors file, but I'm not advanced enough to be able to read it. Can anyone help me out?

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-sz1aUv
GNOME_KEYRING_CONTROL=/tmp/keyring-sz1aUv
SSH_AUTH_SOCK=/tmp/keyring-sz1aUv/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-sz1aUv
SSH_AUTH_SOCK=/tmp/keyring-sz1aUv/ssh

(polkit-gnome-authentication-agent-1:1265): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1265): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:1261): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x813cc38'
Starting Dropbox...** (nm-applet:1263): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.2
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
** (nm-applet:1263): DEBUG: foo_client_state_changed_cb
Unable to open desktop file /home/liam/Desktop/gnome-terminal.desktop for panel launcher: No such file or directory

(nm-applet:1263): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
Dropbox isn't running!
Done!
** (nm-applet:1263): DEBUG: foo_client_state_changed_cb
I/O warning : failed to load external entity "/home/liam/.compiz/session/10a1056177b872e9ef127541725735025600000012000027"
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
evolution-alarm-notify-Message: Setting timeout for 19510 1275436800 1275417290
evolution-alarm-notify-Message:  Tue Jun  1 17:00:00 2010

evolution-alarm-notify-Message:  Tue Jun  1 11:34:50 2010

** (update-notifier:1546): DEBUG: Skipping reboot required
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

---

### Post by LiamG on 2010-06-04
If nobody can help then could somebody point me in a direction where I might be able to find help? I have to kill the power on my laptop 10-15 per day right now, which is probably doing it no good at all.

---

