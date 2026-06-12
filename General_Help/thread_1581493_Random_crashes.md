---
title: "Random crashes"
date: 2010-09-25
forum: General Help
---

### Post by toffuuu on 2010-09-25
I'm nbot sure exactly as to what is causing this and I'm not sure which log to look at either, but I seem to be experiencing just a crash of the entire system, then it goes back to line blinking and rebooting the log in window, and well all is fine then  until it happens again...  I am using 32 Bit 10.04 on 64 Bit machine, and  for logs please let me know which logs i should look into, and i will also copy and post it on here as well...

---

### Post by toffuuu on 2010-09-25
> **toffuuu said:**
> I'm nbot sure exactly as to what is causing this and I'm not sure which log to look at either, but I seem to be experiencing just a crash of the entire system, then it goes back to line blinking and rebooting the log in window, and well all is fine then  until it happens again...  I am using 32 Bit 10.04 on 64 Bit machine, and  for logs please let me know which logs i should look into, and i will also copy and post it on here as well...

thought i would include this from home folder/.xsession-errors

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-I1S8uT
GNOME_KEYRING_CONTROL=/tmp/keyring-I1S8uT
SSH_AUTH_SOCK=/tmp/keyring-I1S8uT/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-I1S8uT

(polkit-gnome-authentication-agent-1:8630): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:8630): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:8618): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x8f89d18'
Initializing nautilus-gdu extension
Starting gtk-window-decorator
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Unable to find a synaptics device.
I/O warning : failed to load external entity "/home/zerocool/.compiz/session/1051fdfe9db0d3fb1c128539499318981800000085560026"
evolution-alarm-notify-Message: Setting timeout for 82177 1285477200 1285395023
evolution-alarm-notify-Message:  Sun Sep 26 00:00:00 2010

evolution-alarm-notify-Message:  Sat Sep 25 01:10:23 2010

** (update-notifier:8825): DEBUG: Skipping reboot required

---

