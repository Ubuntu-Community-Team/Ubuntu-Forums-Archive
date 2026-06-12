---
title: "Ubuntu 10.04 wrong theme"
date: 2010-05-15
forum: General Help
---

### Post by tombaugh on 2010-05-15
I recently installed 10.04 and changed the theme to Radiance. Now suddenly Ubuntu starts with the theme below, although sometimes the panel looks allright. Everything looks fine on very rare occasions. 

An additional problem is that the keyring dialog doesn't come up anymore and I have to connect to wireless manually.

[IMG]http://i40.tinypic.com/2qu5ezt.png[/IMG]

---

### Post by tombaugh on 2010-05-15
.xsession-errors
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-iLRXva
GNOME_KEYRING_PID=1196
GNOME_KEYRING_CONTROL=/tmp/keyring-iLRXva
GNOME_KEYRING_CONTROL=/tmp/keyring-iLRXva
SSH_AUTH_SOCK=/tmp/keyring-iLRXva/ssh
Window manager warning: Failed to read saved session file /home/pieter/.config/metacity/sessions/10cf0dc6eb74048f10127391669884689400000011500030.ms: Failed to open file '/home/pieter/.config/metacity/sessions/10cf0dc6eb74048f10127391669884689400000011500030.ms': No such file or directory

(polkit-gnome-authentication-agent-1:1234): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1234): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (nm-applet:1225): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1225): DEBUG: old state indicates that this was not a disconnect 0
Starting Dropbox...Initializing nautilus-dropbox 0.6.2
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension

(gnome-power-manager:1235): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.0/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x9f874e0'

** (gnome-power-manager:1235): WARNING **: Either HAL or DBUS are not working!

** (gnome-power-manager:1235): WARNING **: proxy failed

** (gnome-power-manager:1235): WARNING **: failed to get Computer root object

** (gnome-power-manager:1235): WARNING **: proxy NULL!!
Unable to find a synaptics device.
Dropbox isn't running!
Done!

(nautilus:1227): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(gnome-panel:1223): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gvfs/gvfs-gdu-volume-monitor received signal 6

(gnome-settings-daemon:1198): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gvfs/gvfs-gdu-volume-monitor received signal 6
The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 820 error_code 8 request_code 3 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

/bin/sh: ubuntuone-launch: not found
evolution-alarm-notify-Message: Setting timeout for 51271 1273968000 1273916729
evolution-alarm-notify-Message:  Sun May 16 02:00:00 2010

evolution-alarm-notify-Message:  Sat May 15 11:45:29 2010

** (update-notifier:1509): DEBUG: Skipping reboot required
** (nm-applet:1225): DEBUG: foo_client_state_changed_cb
** (nm-applet:1225): DEBUG: foo_client_state_changed_cb
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

---

### Post by sidneylopsides on 2010-05-15
My theme has started doing that, the window frames and menu bars go back to the Ambiance theme as soon as I try to open appearance Prefs, but the navigation buttons etc stay looking, well, naff.

---

### Post by golog on 2010-05-29
Same here:

every time I start the PC the window frames, icons in file browser and menu bars go back to some old & ugly theme.

As soon as I try to open Appearance Prefs, the normal theme comes back. File browser still looking old, and I cannot change its style :(

(I had a clean install, no upgrade. If somebody would ask)

No problem here with the keyring.

---

### Post by meho_r on 2010-05-29
Happens to me from time to time too, sometimes when I close an application theme simply breaks, sometimes systems starts with "wrong" theme. After opening **Appearance** settings, it changes back to "normal" theme, but for completely restoring the theme, I must **killall nautilus**.

This seems like a bug to me, maybe OP should report it?

---

### Post by meho_r on 2010-05-31
This is really frustrating. Yesterday it started breaking the theme every single time after (re)start. I removed settings related to metacity/panels/etc., no avail. But now comes the interesting thing: I removed AWN from StartUp Applications, and after a restart, the theme was correct. Started AWN and set it again to start automatically, then restarted the computer, was fine. Hope it'll stay this way.

---

### Post by sidneylopsides on 2010-05-31
hmm, I don't have AWN, mine is a clean install, I've not changed any themes, all I've done is install compiz settings manager so I can have the cube desktop. Mine looses the window themes every startup.

---

### Post by meho_r on 2010-06-01
And I had problems with Compiz disabled too, so I'm not sure if it's causing the trouble :(

---

### Post by dtzortzis on 2010-06-02
I'm having the same issue. I still don't know where it's coming from. Glad to see it's not only my problem! Check out these two threads:
[http://ubuntuforums.org/showthread.php?t=1384470](http://ubuntuforums.org/showthread.php?t=1384470)
[http://ubuntuforums.org/showthread.php?t=1485102](http://ubuntuforums.org/showthread.php?t=1485102)

And this one too:
[http://ubuntuforums.org/showthread.php?t=1449832](http://ubuntuforums.org/showthread.php?t=1449832)

---

### Post by golog on 2010-06-16
removed wicd, problem was gone

---

### Post by sidneylopsides on 2010-06-16
I think I want to keep that, isn't that my network manager interface?

---

### Post by meho_r on 2010-06-24
> **golog said:**
> removed wicd, problem was gone

No wicd here, problem persisted (not necessary every time on startup, but theme still does breaks from time to time). Gnome-settings-daemon crash is the cause. I filed a bug against gnome-settings-daemon [here](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/598009).

---

### Post by belfi117 on 2010-07-23
Hi. The same problem here. Everything goes back to normal as soon as I open Pref./Appearance, except file browser. When I restart file browser ($nautilus -q) it becomes OK. Still it's not a solution for this bug, but gets rid of that ugly theme up to the next crash!

---

