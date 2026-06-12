---
title: "Xsession-errors - failed to load .compiz"
date: 2010-05-05
forum: General Help
---

### Post by BrokeMahPC on 2010-05-05
I have had a few X crashes and started to suspect compiz as they usually happened when I was resizing a window or the window was wobbling.

Here is the Xsession-errors log (it's a hidden file in your home folder). It mentions:
```
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
Unable to find a synaptics device.
I/O warning : failed to load external entity "/home/user06/.compiz/session/102fbbaf9a6d9a04a2127304455015063700000020030032"
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
```Anything I can do about this failing to load .compiz? (If it's relevant) I kept my /home partition from a previous install. Can I delete the contents of .compiz and reconfigure and reset compiz somehow?

Full output of Xsession-errors:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-PczeBL
GNOME_KEYRING_CONTROL=/tmp/keyring-PczeBL
SSH_AUTH_SOCK=/tmp/keyring-PczeBL/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-PczeBL
SSH_AUTH_SOCK=/tmp/keyring-PczeBL/ssh

(polkit-gnome-authentication-agent-1:2100): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2100): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:2090): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.0/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x8da28f8'
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
Initializing nautilus-gdu extension
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
Unable to find a synaptics device.
I/O warning : failed to load external entity "/home/user06/.compiz/session/108412585f4d1d999e127307243891172000000020190032"
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
evolution-alarm-notify-Message: Setting timeout for 31531 1273104000 1273072469
evolution-alarm-notify-Message:  Thu May  6 01:00:00 2010

evolution-alarm-notify-Message:  Wed May  5 16:14:29 2010

** (update-notifier:2260): DEBUG: Skipping reboot required
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

---

### Post by dino99 on 2010-05-06
seem to be a nice compiz mess: remove/purge it then reinstall

sudo dpkg --configure -a
sudo apt-get install -f

in general, take care of some not well trusted ppa or third party (build not certified and made by newbies)

---

### Post by BrokeMahPC on 2010-05-07
Thanks Dino - removed every trace of compiz and then reinstalled and it worked. Other problems remain - I'm not sure keeping the home folder and restoring your settings from it is a good idea - for upgrades anyway! It probably does work if reinstalling the same release.
Anyone know of any documentation on this?

---

### Post by ratxor on 2010-11-27
> **BrokeMahPC said:**
> 
I/O warning : failed to load external entity "/home/user06/.compiz/session/102fbbaf9a6d9a04a2127304455015063700000020030032"


I have similar issue with Ubuntu 10.10 Netbook. Compiz works properly, but in ~/.xsession-errors the following warning appeares:
"I/O warning : failed to load external entity "/home/val/.compiz/session/<filename>".
There is no such file in ~/.compiz/session/ folder. Is this issue or not? How to solve it?

---

