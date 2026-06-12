---
title: "Stuck on Command line - no gui - unable to start xorg?"
date: 2011-04-02
forum: General Help
---

### Post by Danial on 2011-04-02
Hi,

Thanks in advance for looking into this issue.

Last night my system rebooted and dropped screen resolution to 800*600. I was unable to change that from no where.  I tried to install nvidia driver and now no gui, only command line. Starting xorg by using 'startx' fails.  How I can get back to normal with normal resolution?

At the moment I am logged in via live cd. Let me know if any log files needed (if I can locate those). I was able to get only these following log files (not sure if needed here).

 .xsession-errors.old

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-lNWLdq
GNOME_KEYRING_CONTROL=/tmp/keyring-lNWLdq
GNOME_KEYRING_CONTROL=/tmp/keyring-lNWLdq
SSH_AUTH_SOCK=/tmp/keyring-lNWLdq/ssh

(polkit-gnome-authentication-agent-1:1597): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1597): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
Unable to find a synaptics device.
Initializing nautilus-gdu extension
Starting gtk-window-decorator

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: applet now embedded in the notification area
I/O warning : failed to load external entity "/home/abba/.compiz/session/106ed697c76a60f3d1130174454996610300000015250027"

(gnome-display-properties:1743): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:1743): Gtk-WARNING **: No object called: 
** (update-notifier:1752): DEBUG: aptdaemon on bus: 0
** (update-notifier:1752): DEBUG: Skipping reboot required

(yelp:1874): Yelp-WARNING **: Failed to load config file: No such file or directory


(yelp:1874): Gtk-CRITICAL **: IA__gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(yelp:1874): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(yelp:1874): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(yelp:1874): Gtk-CRITICAL **: IA__gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

(yelp:1874): Gtk-CRITICAL **: IA__gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(yelp:1874): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(yelp:1874): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(yelp:1874): Gtk-CRITICAL **: IA__gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

** (nautilus:1602): WARNING **: bookmark uri is file:///, but expected file:///usr

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

** (update-notifier:1752): WARNING **: log file empty (logrotate?) /var/log/dpkg.log


** (update-notifier:1752): WARNING **: log file empty (logrotate?) /var/log/apt/term.log


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1602): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
NOTE: child process received `Goodbye', closing down
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

** (gnome-settings-daemon:1572): WARNING **: Connection failed, reconnecting...
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"

      after 355150 requests (355148 known processed) with 41 events remaining.

** Message: Got disconnected from the session message bus; retrying to reconnect every 10 seconds
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
[COLOR=Purple]The application 'gnome-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application[/COLOR].
```{ well highlighted part says a lot for me...I am still a newbie and learning }

and 

 .xsession-errors

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-Kh5KZP
GNOME_KEYRING_CONTROL=/tmp/keyring-Kh5KZP
GNOME_KEYRING_CONTROL=/tmp/keyring-Kh5KZP
SSH_AUTH_SOCK=/tmp/keyring-Kh5KZP/ssh

(polkit-gnome-authentication-agent-1:1599): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1599): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
Unable to find a synaptics device.
Initializing nautilus-gdu extension
Starting gtk-window-decorator

(nautilus:1604): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: applet now embedded in the notification area
I/O warning : failed to load external entity "/home/abba/.compiz/session/10ca8f661d87be523f130176493731795200000015270027"
** (update-notifier:1807): DEBUG: --security-updates-unattended: 0

** (update-notifier:1807): DEBUG: aptdaemon on bus: 0
** (update-notifier:1807): DEBUG: Skipping reboot required
x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(gnome-panel:1605): GLib-GObject-CRITICAL **: g_object_run_dispose: assertion `G_IS_OBJECT (object)' failed
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
firefox-bin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Window manager error: Unable to open X display :0.0
```So where do I start/go now...

Danial

---

### Post by Danial on 2011-04-02
Hmmm - no response - this is strange]

Is this post like this ](*,) or I just did not ask the right question?

Danial

---

### Post by matt_symes on 2011-04-02
Hi

> **Danial said:**
> Hmmm - no response - this is strange]

Is this post like this ](*,) or I just did not ask the right question?

Danial

Please be patient. Different people with different skills come onto the forums all the time.

So this was the timeline of events?

1. You Reboot your PC.
2. Your system only displays 800x600 resolution after starting up.
3. You try to fix this by installing the nvidia drivers.
4. You reboot and it goes straight to the command line log in.

Is this correct ?

Where did you get the drivers from ?

Maybe this is not my area but i would suggest you post your Xorg.0.log file. Its location is

```
/var/log/Xorg.0.log
```

Also, post your xorg.conf file if you have one. Its location is 

```
/etc/X11/xorg.conf
```

That will give people a place to start.

Kind regards

---

### Post by Danial on 2011-04-03
> **matt_symes said:**
> Hi

So this was the timeline of events?

1. You Reboot your PC.
2. Your system only displays 800x600 resolution after starting up.
3. You try to fix this by installing the nvidia drivers.
4. You reboot and it goes straight to the command line log in.

Is this correct ?

Where did you get the drivers from ?

Maybe this is not my area but i would suggest you post your Xorg.0.log file. Its location is

```
/var/log/Xorg.0.log
```

Also, post your xorg.conf file if you have one. Its location is 

```
/etc/X11/xorg.conf
```

That will give people a place to start.

Kind regards


Matt, 

Sorry, I did not mean to be rude to anyone. I realize those were not the right words though, my bad.

**_Timeline:_**


**1.** PC was logged on to Win7 and screensaver was active. After a while, I noticed that system was rebooted.  Since Ubuntu 10.10 is first on the grub menu.lst, it booted to ubuntu with 800*600 resolution. I have no idea, how a crash on Win7 may affects the ubuntu side (if that is really the case - however, I had a similar experience in the past and I had to re-install Maverick after updating the BIOS).
**2.** Resolution fall to 800*600 and was unable to adjust/change from display setting or from nvidia utility. 800*600 was the highest available in both places. At the same time, Visual Effects in Appearance Preference were still on 'Normal'.  I rebooted pc for few many times to no avail, recovery mode was also in low res. Win7 apparently came to normal after prompting to boot normally.
**3.** I downloaded driver from nvidia site. Originally, I had installed  ubuntu restricted driver (current and recommended version). As per instructions (nvidia site), I stopped the xserver and load the driver from a floppy. Once the installation finished, rebooted - and that is the end of the story. I tried 'startx' from the shell to no avail. 
**4.** Now, I only get to command line login. 

Following are the outputs for xorg.conf and xorg.x.log. I also included the previous log (1), just in case.  As far as I remember, this xorg.conf is same as I had before this incident.  

**xorg.conf:**

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

 
**Xorg.0.log:**
```
[    11.620] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    11.620] X Protocol Version 11, Revision 0
[    11.620] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    11.620] Current Operating System: Linux abba-System-desktop 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686
[    11.620] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=UUID=53d3316a-5582-46f0-b665-aa3ab3409057 ro quiet splash
[    11.620] Build Date: 09 January 2011  12:14:58PM
[    11.620] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    11.620] Current version of pixman: 0.18.4
[    11.620] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    11.620] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.620] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr  2 14:03:30 2011
[    11.621] (==) Using config file: "/etc/X11/xorg.conf"
[    11.621] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.621] (==) No Layout section.  Using the first Screen section.
[    11.621] (**) |-->Screen "Default Screen" (0)
[    11.621] (**) |   |-->Monitor "<default monitor>"
[    11.621] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    11.621] (**) |   |-->Device "Default Device"
[    11.621] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    11.621] (==) Automatically adding devices
[    11.621] (==) Automatically enabling devices
[    11.655] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.655] 	Entry deleted from font path.
[    11.669] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    11.669] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.669] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.669] (II) Loader magic: 0x81f9b00
[    11.669] (II) Module ABI versions:
[    11.669] 	X.Org ANSI C Emulation: 0.4
[    11.669] 	X.Org Video Driver: 8.0
[    11.669] 	X.Org XInput driver : 11.0
[    11.669] 	X.Org Server Extension : 4.0
[    11.670] (--) PCI:*(0:0:5:0) 10de:0240:147b:1c26 rev 162, Mem @ 0xfc000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, BIOS @ 0x????????/131072
[    11.671] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.671] (II) "extmod" will be loaded by default.
[    11.671] (II) "dbe" will be loaded by default.
[    11.671] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    11.671] (II) "record" will be loaded by default.
[    11.671] (II) "dri" will be loaded by default.
[    11.671] (II) "dri2" will be loaded by default.
[    11.671] (II) LoadModule: "glx"
[    11.674] (WW) Warning, couldn't open module glx
[    11.674] (II) UnloadModule: "glx"
[    11.674] (EE) Failed to load module "glx" (module does not exist, 0)
[    11.674] (II) LoadModule: "extmod"
[    11.674] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.674] (II) Module extmod: vendor="X.Org Foundation"
[    11.674] 	compiled for 1.9.0, module version = 1.0.0
[    11.674] 	Module class: X.Org Server Extension
[    11.674] 	ABI class: X.Org Server Extension, version 4.0
[    11.674] (II) Loading extension MIT-SCREEN-SAVER
[    11.674] (II) Loading extension XFree86-VidModeExtension
[    11.674] (II) Loading extension XFree86-DGA
[    11.674] (II) Loading extension DPMS
[    11.674] (II) Loading extension XVideo
[    11.674] (II) Loading extension XVideo-MotionCompensation
[    11.674] (II) Loading extension X-Resource
[    11.674] (II) LoadModule: "dbe"
[    11.674] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.674] (II) Module dbe: vendor="X.Org Foundation"
[    11.674] 	compiled for 1.9.0, module version = 1.0.0
[    11.674] 	Module class: X.Org Server Extension
[    11.674] 	ABI class: X.Org Server Extension, version 4.0
[    11.674] (II) Loading extension DOUBLE-BUFFER
[    11.674] (II) LoadModule: "record"
[    11.675] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.675] (II) Module record: vendor="X.Org Foundation"
[    11.675] 	compiled for 1.9.0, module version = 1.13.0
[    11.675] 	Module class: X.Org Server Extension
[    11.675] 	ABI class: X.Org Server Extension, version 4.0
[    11.675] (II) Loading extension RECORD
[    11.675] (II) LoadModule: "dri"
[    11.675] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.675] (II) Module dri: vendor="X.Org Foundation"
[    11.675] 	compiled for 1.9.0, module version = 1.0.0
[    11.675] 	ABI class: X.Org Server Extension, version 4.0
[    11.675] (II) Loading extension XFree86-DRI
[    11.675] (II) LoadModule: "dri2"
[    11.675] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.675] (II) Module dri2: vendor="X.Org Foundation"
[    11.675] 	compiled for 1.9.0, module version = 1.2.0
[    11.675] 	ABI class: X.Org Server Extension, version 4.0
[    11.676] (II) Loading extension DRI2
[    11.676] (II) LoadModule: "nvidia"
[    11.676] (WW) Warning, couldn't open module nvidia
[    11.676] (II) UnloadModule: "nvidia"
[    11.676] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    11.676] (EE) No drivers available.
[    11.676] 
Fatal server error:
[    11.676] no screens found
[    11.676] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    11.676] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    11.676] 
```

**Xorg.1.log:**
```
[    11.717] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    11.717] X Protocol Version 11, Revision 0
[    11.717] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    11.717] Current Operating System: Linux abba-System-desktop 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686
[    11.717] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=UUID=53d3316a-5582-46f0-b665-aa3ab3409057 ro quiet splash
[    11.717] Build Date: 09 January 2011  12:14:58PM
[    11.717] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    11.717] Current version of pixman: 0.18.4
[    11.717] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    11.717] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.717] (==) Log file: "/var/log/Xorg.1.log", Time: Sat Apr  2 14:03:30 2011
[    11.717] (==) Using config file: "/etc/X11/xorg.conf"
[    11.717] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.718] (==) No Layout section.  Using the first Screen section.
[    11.718] (**) |-->Screen "Default Screen" (0)
[    11.718] (**) |   |-->Monitor "<default monitor>"
[    11.718] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    11.718] (**) |   |-->Device "Default Device"
[    11.718] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    11.718] (==) Automatically adding devices
[    11.718] (==) Automatically enabling devices
[    11.718] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.718] 	Entry deleted from font path.
[    11.718] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    11.718] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.718] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.718] (II) Loader magic: 0x81f9b00
[    11.718] (II) Module ABI versions:
[    11.718] 	X.Org ANSI C Emulation: 0.4
[    11.718] 	X.Org Video Driver: 8.0
[    11.718] 	X.Org XInput driver : 11.0
[    11.718] 	X.Org Server Extension : 4.0
[    11.719] (--) PCI:*(0:0:5:0) 10de:0240:147b:1c26 rev 162, Mem @ 0xfc000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, BIOS @ 0x????????/131072
[    11.719] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.719] (II) "extmod" will be loaded by default.
[    11.719] (II) "dbe" will be loaded by default.
[    11.719] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    11.719] (II) "record" will be loaded by default.
[    11.720] (II) "dri" will be loaded by default.
[    11.720] (II) "dri2" will be loaded by default.
[    11.720] (II) LoadModule: "glx"
[    11.721] (WW) Warning, couldn't open module glx
[    11.721] (II) UnloadModule: "glx"
[    11.721] (EE) Failed to load module "glx" (module does not exist, 0)
[    11.721] (II) LoadModule: "extmod"
[    11.721] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.721] (II) Module extmod: vendor="X.Org Foundation"
[    11.721] 	compiled for 1.9.0, module version = 1.0.0
[    11.721] 	Module class: X.Org Server Extension
[    11.721] 	ABI class: X.Org Server Extension, version 4.0
[    11.721] (II) Loading extension MIT-SCREEN-SAVER
[    11.721] (II) Loading extension XFree86-VidModeExtension
[    11.721] (II) Loading extension XFree86-DGA
[    11.721] (II) Loading extension DPMS
[    11.721] (II) Loading extension XVideo
[    11.721] (II) Loading extension XVideo-MotionCompensation
[    11.721] (II) Loading extension X-Resource
[    11.721] (II) LoadModule: "dbe"
[    11.721] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.722] (II) Module dbe: vendor="X.Org Foundation"
[    11.722] 	compiled for 1.9.0, module version = 1.0.0
[    11.722] 	Module class: X.Org Server Extension
[    11.722] 	ABI class: X.Org Server Extension, version 4.0
[    11.722] (II) Loading extension DOUBLE-BUFFER
[    11.722] (II) LoadModule: "record"
[    11.722] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.722] (II) Module record: vendor="X.Org Foundation"
[    11.722] 	compiled for 1.9.0, module version = 1.13.0
[    11.722] 	Module class: X.Org Server Extension
[    11.722] 	ABI class: X.Org Server Extension, version 4.0
[    11.722] (II) Loading extension RECORD
[    11.722] (II) LoadModule: "dri"
[    11.722] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.722] (II) Module dri: vendor="X.Org Foundation"
[    11.722] 	compiled for 1.9.0, module version = 1.0.0
[    11.722] 	ABI class: X.Org Server Extension, version 4.0
[    11.722] (II) Loading extension XFree86-DRI
[    11.722] (II) LoadModule: "dri2"
[    11.723] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.723] (II) Module dri2: vendor="X.Org Foundation"
[    11.723] 	compiled for 1.9.0, module version = 1.2.0
[    11.723] 	ABI class: X.Org Server Extension, version 4.0
[    11.723] (II) Loading extension DRI2
[    11.723] (II) LoadModule: "nvidia"
[    11.723] (WW) Warning, couldn't open module nvidia
[    11.723] (II) UnloadModule: "nvidia"
[    11.723] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    11.724] (EE) No drivers available.
[    11.724] 
Fatal server error:
[    11.724] no screens found
[    11.724] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    11.724] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    11.724] 
```


I am not using any fancy system and/or settings on this PC. It has 2G ram; Abit motherboard with nvidia 6150 onboard;2 HD - sata is boot drive for both OSes. 

Just come to my mind that my monitor is connected via dvi and I had not tried to connect it via dsub (but I guess that would not make much of a difference since xorg.0.log shows error for not finding the drivers and modules. What do I know.

If there is any other info I need to provide, please let me know.

Thanks, 
Danial

---

### Post by matt_symes on 2011-04-03
Hi

> since xorg.0.log shows error for not finding the drivers and modules

```
[    11.671] (II) LoadModule: "glx"
[    11.674] (WW) Warning, couldn't open module glx
[    11.674] (II) UnloadModule: "glx"
[    11.674] (EE) Failed to load module "glx" (module does not exist, 0)

...

[    11.676] (II) LoadModule: "nvidia"
[    11.676] (WW) Warning, couldn't open module nvidia
[    11.676] (II) UnloadModule: "nvidia"
[    11.676] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    11.676] (EE) No drivers available.
```

You're quite right. It's looking for the nvidia drivers and cannot find them. It is then bailing out.

Can you boot into fail safe graphics mode ? 

How did you install the drivers ? I'm not sure what state your PC is in as it's looking for drivers it can't find.

Do you have a link to the site you got them from ?

First thing i would try is to reconfigure xorg.

```
sudo dpkg-reconfigure xserver-xorg -priority=high
```

If that does not work i would look at purging the nvidia driver if it is still there and using xforcevesa kernel switch or creating a new xorg.conf to boot using vesa and trying to establish what went wrong and what state the PC is in.

Kind regards

---

### Post by chinmay3 on 2011-04-03
once i have same problem. I tried different methods but none worked . then found someone have same problem due improperly connected monitor cable. then I reconnected mine too & problem get solved. 
Try this , may work !:P

---

### Post by Danial on 2011-04-03
> **chinmay3 said:**
> once i have same problem. I tried different methods but none worked . then found someone have same problem due improperly connected monitor cable. then I reconnected mine too & problem get solved. 
Try this , may work !:P


Thanks for the tip. Yes I did check the cable on both end - actually unplug and plug again just to make sure no oxidation effects (unlikely though). Win7 and LiveCD are connecting fine with same cable. I am using LiveCD as we speak. I can always try another cable, that won't hurt. Once again thanks for your help and time. 

Danial

---

### Post by wolfen69 on 2011-04-03
If you can get to a command line of any sort, try
```
sudo nvidia-xconfig
```
then 
```
sudo reboot
```

---

### Post by Danial on 2011-04-03
> **matt_symes said:**
> Hi

> Can you boot into fail safe graphics mode ? 
Let me try again after posting this message.

[QUOTE]Do you have a link to the site you got them from ?
[nvidia drivers]("http://www.nvidia.com/object/linux-display-ia32-260.19.44-driver.html")
[http://www.nvidia.com/object/linux-display-ia32-260.19.44-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.44-driver.html)


> First thing i would try is to reconfigure xorg.
```
sudo dpkg-reconfigure xserver-xorg -priority=high
```
I understand, I do it from the shell but is there any specific parameters I need to enter? I don't know any beside the one I see in my current xorg.conf file. Once it is done, do I need to reboot or just restart xserver by using 'startx' from the command prompt??  And this leads to your following comment that should I try to purge old driver first?

> How did you install the drivers ? I'm not sure what state your PC is in as it's looking for drivers it can't find.
> If that does not work i would look at purging the nvidia driver if it is still there and using xforcevesa kernel switch or creating a new xorg.conf to boot using vesa and trying to establish what went wrong and what state the PC is in.
I am not sure either about what state it is in? I think that system is trying to boot with vesa and not able to complete that task. Having said that, I guess, there is still some leftover from the nvidia driver installation and that need to be purge properly.  So if I want to do that, how do I do it from shell? 

Matt, thanks a lot for your time and patience with me. When you get few minutes, please respond. 

Regards,
Danial

---

### Post by matt_symes on 2011-04-03
Hi

I made a slight typo. You need to enter --priority=

```
sudo dpkg-reconfigure xserver-xorg --priority=high
```

I would also try wolfen69's idea. That is an excellent suggestion.

The first will try to reconfigure xorg and the second will regenerate your nvidia settings.

IIRC, neither will require parameters. It's been a long while since i have used either.

You need to boot into either failsafe graphics mode or to the command line. 

You can boot into the command line by selecting a recovery kernel and then selecting the root console option. You will not require sudo if using the root console.

If neither of them work, we will have to dig deeper.

Kind regards

---

### Post by Danial on 2011-04-03
> **wolfen69 said:**
> If you can get to a command line of any sort, try
```
sudo nvidia-xconfig
```
then 
```
sudo reboot
```

> **matt_symes said:**
> Hi

```
sudo dpkg-reconfigure xserver-xorg --priority=high
```

I would also try wolfen69's idea. That is an excellent suggestion.

The first will try to reconfigure xorg and the second will regenerate your nvidia settings.

IIRC, neither will require parameters. It's been a long while since i have used either.

You need to boot into either failsafe graphics mode or to the command line. 

You can boot into the command line by selecting a recovery kernel and then selecting the root console option. You will not require sudo if using the root console.

If neither of them work, we will have to dig deeper.

Kind regards

Matt and Wolfen69,

Thanks for your input.

I tried both above mentioned codes and got following errors:
when I did sudo dpkg-reconfigure ..., I got "x-server-xorg  not installed and no info available"

and when I tried nvidia-xconfig I got 
Validation Error: Data incomplete in file /etc/X11/Xorg.conf
Undefined device "(nul)" referenced by Screen "Default Screen". Backedup file xorg.conf xorg.conf.backup. New X configuration file written to xorg.conf.

After that I tried to log in to failsafe graphics mode. That was also unsuccessful. errors: failed to load module 'glx', no valid nodes, screens found but none have a usable configuration. fatal server error.  log file: /var/log/Xorg.failsafe.log.

I will include that file with xorg.conf and xorg.0.log in my next post (I am logged in to Windows and can not access those - but I wanted to post at least some info). I guess you may not be able to look any further without those files. Sorry about that.

Regards,
Danial

---

### Post by matt_symes on 2011-04-04
> **Danial said:**
> 

I tried both above mentioned codes and got following errors:
when I did sudo dpkg-reconfigure ..., I got "x-server-xorg  not installed and no info available"

Did you type in this ?

```
sudo dpkg-reconfigure x**-**server-xorg --priority=high
```

It should have been this.

```
sudo dpkg-reconfigure xserver-xorg --priority=high
```

> 
After that I tried to log in to failsafe graphics mode. That was also unsuccessful. errors: failed to load module 'glx', no valid nodes, screens found but none have a usable configuration. fatal server error.  log file: /var/log/Xorg.failsafe.log.

Those logs would help.

What i think we should do it rename the xorg.conf file. It is referencing glx and the system cannot find glx for what ever reason. 

We should then boot using vesa to get to a desktop and then try to purge any references to the Nvidia driver.

So from the console.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Reboot the PC and at the grub menu select you kernel and press **e** to edit the kernel command line.

Look for the line that says something similar to (your boot_image and uuid may be different)

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=3d48429c-7361-4ab8-8689-54407673b141 ro quiet splash
```

and add the word xforcevesa to the line so it becomes

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=3d48429c-7361-4ab8-8689-54407673b141 ro quiet splash xforcevesa
```

Press ctrl + x to boot. Hopefully that will boot you into a gui where things may be easier for you. This will not persist after reboots.

Next lets purge the nvidia driver you installed.

```
sudo apt-get remove --purge *<name_of_nvidia_driver>*
```

Someting along the lines of (LOWER CASE DPKG -L | ...) 

```
dpkg -l | grep -i nvidia
```

should tell you the driver name you installed. I don't use nvidia.

How do all that go so far ? If that has gone well we can look at reinstalling the driver correctly.

Kind regards

---

