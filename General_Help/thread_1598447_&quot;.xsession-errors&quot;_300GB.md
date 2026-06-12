---
title: "&quot;.xsession-errors&quot; 300GB"
date: 2010-10-16
forum: General Help
---

### Post by Dajax on 2010-10-16
Can I just delete this file... it is 300GB and my hard drive now only has 1gb left..
I just installed ubuntu two days ago...


Thanks

---

### Post by dtfinch on 2010-10-16
You'll want to reboot (or maybe just log out and back in) after you delete it, because if it's still open the space won't be freed until then.

And it'd help to know what error it's been logging billions of times in order to make it stop.

---

### Post by Dajax on 2010-10-16
I opened it to see and it slowed my computer to a halt... 

I will delete it restart and look to see what it has in it, and post it here.. or paste bin depending on size.

I just wasn't sure deleting it would be sound.

---

### Post by Dajax on 2010-10-16
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-86TGDg
GNOME_KEYRING_PID=1396
GNOME_KEYRING_CONTROL=/tmp/keyring-86TGDg
GNOME_KEYRING_CONTROL=/tmp/keyring-86TGDg
SSH_AUTH_SOCK=/tmp/keyring-86TGDg/ssh

(polkit-gnome-authentication-agent-1:1520): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1520): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
Initializing nautilus-gdu extension

(nautilus:1518): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Unable to find a synaptics device.
** Message: applet now embedded in the notification area

(nm-applet:1515): Gdk-CRITICAL **: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
Starting gtk-window-decorator
I/O warning : failed to load external entity "/home/josh/.compiz/session/1071ac714283f02a8b128725584296734100000013500027"
** (update-notifier:1635): DEBUG: --security-updates-unattended: 0

** (update-notifier:1635): DEBUG: aptdaemon on bus: 0
** (update-notifier:1635): DEBUG: Skipping reboot required

(nautilus:1518): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1518): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```


The only thing I have done is Startup Login and Empty trash again... It didn't empty before I logged out.

---

