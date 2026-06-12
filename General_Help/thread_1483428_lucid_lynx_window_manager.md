---
title: "lucid lynx window manager??"
date: 2010-05-14
forum: General Help
---

### Post by gfunkera on 2010-05-14
since i upgraded to lucid lynx, ubuntu boots up without a window manager running... how do i fix this?

this is what was happening: 
- chrome cant be resized even if the maximize button is pressed
- firefox doesnt have any minimize/maximize, etc. buttons.. it just opens and is fixed in size (in fact that whole title bar at the top is missing)
- the "show desktop" button comes back with an error that says that there is no window manager running

---

### Post by _0R10N on 2010-05-14
> **gfunkera said:**
> since i upgraded to lucid lynx, ubuntu boots up without a window manager running... how do i fix this?

this is what was happening: 
- chrome cant be resized even if the maximize button is pressed
- firefox doesnt have any minimize/maximize, etc. buttons.. it just opens and is fixed in size (in fact that whole title bar at the top is missing)
- the "show desktop" button comes back with an error that says that there is no window manager running

Wow! that's pretty odd. At least, it's the first time I know of such a behavior. Try opening a terminal and running:
```
gnome-session
```
What happens then?

---

### Post by _0R10N on 2010-05-14
You can also check your startup applications configuration and see if nothing important has been disabled. The window is located under your preference menu, or you can simply run:
```
gnome-session-properties
```

Another application I like for checking startup services and applications is Bootup-Manager. If you want to check it out
```
aptitude install bum
```

After installation, it will be available under your Administration menu.

Kind regards!

---

### Post by gfunkera on 2010-05-14
```
myusername@dmachine420:~$ gnome-session
gnome-session[3409]: WARNING: Failed to acquire org.gnome.SessionManager
gnome-session[3409]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed
gnome-session[3409]: WARNING: Could not parse desktop file /home/myusername/.config/autostart/print-applet.desktop: Key file does not have key 'Name'
gnome-session[3409]: WARNING: could not read /home/myusername/.config/autostart/print-applet.desktop
gnome-session[3409]: WARNING: Could not parse desktop file /home/myusername/.config/autostart/xfconf-migration-4.6.desktop: Key file does not have key 'Name'
gnome-session[3409]: WARNING: could not read /home/myusername/.config/autostart/xfconf-migration-4.6.desktop
gnome-session[3409]: WARNING: Could not parse desktop file /home/myusername/.config/autostart/xfce4-settings-helper-autostart.desktop: Key file does not have key 'Name'
gnome-session[3409]: WARNING: could not read /home/myusername/.config/autostart/xfce4-settings-helper-autostart.desktop

** (gnome-settings-daemon:3419): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:3419): WARNING **: Could not acquire name
GNOME_KEYRING_CONTROL=/tmp/keyring-1Qo3jh
SSH_AUTH_SOCK=/tmp/keyring-1Qo3jh/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-1Qo3jh
SSH_AUTH_SOCK=/tmp/keyring-1Qo3jh/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-1Qo3jh
SSH_AUTH_SOCK=/tmp/keyring-1Qo3jh/ssh
gnome-session[3409]: WARNING: Could not launch application '10219b36a5b0172ac5126879290386096300000027660043.desktop': Unable to start application: Failed to execute child process "/usr/bin/compiz.real" (No such file or directory)
Cannot register the panel shell: there is already one running.
Failure: Module initalization failed
gnome-session[3409]: WARNING: Could not launch application 'wicd-tray.desktop': Unable to start application: Failed to execute child process "wicd-client" (No such file or directory)
gnome-session[3409]: WARNING: Could not launch application '10b4e3ca619d1922ec127317623566439700000028820045.desktop': Unable to start application: Failed to execute child process "indicator-applet-session" (No such file or directory)
gnome-session[3409]: WARNING: Could not launch application '10b4e3ca619d1922ec127317618883601900000028820044.desktop': Unable to start application: Failed to execute child process "evolution-exchange-storage" (No such file or directory)
Failed to play sound: Sound disabled
Initializing trackerd...
Tracker-Message: Checking XDG_DATA_HOME is writable and exists
Tracker-Message:   XDG_DATA_HOME is '(null)'
Tracker-Message:   XDG_DATA_HOME set to '/home/myusername/.local/share'
Tracker-Message:   Path is OK
Tracker-Message: Setting IO priority
Tracker-Message: Setting up monitor for changes to config file:'/home/myusername/.config/tracker/tracker.cfg'
Tracker-Message: Loading defaults into GKeyFile...
Tracker-Message: Legacy config option 'IndexEvolutionEmails' found
Tracker-Message:   This option has been replaced by 'DisabledModules'
Tracker-Message:   Option 'DisabledModules' removed 'evolution'
Tracker-Message: Legacy config option 'IndexThunderbirdEmails' found
Tracker-Message:   This option is no longer supported and has no effect
Tracker-Message: Legacy config option 'SkipMountPoints' found
Tracker-Message:   Option 'IndexMountedDirectories' set to true
Tracker-Message: Setting up stopword list for language code:'en'

(polkit-gnome-authentication-agent-1:3447): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:3447): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (polkit-gnome-authentication-agent-1:3447): WARNING **: Unable to register authentication agent: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.RegisterAuthenticationAgent() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
Cannot register authentication agent: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.RegisterAuthenticationAgent() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session

MCS->Xfconf settings migration complete

An instance of nm-applet is already running.

** (nm-applet:3448): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

evolution-alarm-notify-Message: Setting timeout for 30304 1273899600 1273869296
evolution-alarm-notify-Message:  Sat May 15 00:00:00 2010

evolution-alarm-notify-Message:  Fri May 14 15:34:56 2010


(evolution-alarm-notify:3441): evolution-alarm-notify-WARNING **: Could not create the alarm notify service factory, maybe it's already running...

(gnome-power-manager:3446): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.0/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x99f9700'
Tracker-Message: Setting up stemmer for language code:'en'
Tracker-Message: Checking directory exists:'/home/myusername/.local/share/tracker/data'
Tracker-Message: Checking directory exists:'/home/myusername/.cache/tracker'
Tracker-Message: Registering DBus service...
  Name:'org.freedesktop.Tracker'

(trackerd:3449): Tracker-CRITICAL **: DBus service name:'org.freedesktop.Tracker' is already taken, perhaps the daemon is already running?
TI:15:34:57	TH:0x999d6d8	FI:gpm-main.c	FN:main,250
 - Power Manager is already running in this session.
Traceback:
	gnome-power-manager() [0x806487b]
	gnome-power-manager() [0x80574b2]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xff2bd6]
	gnome-power-manager() [0x804ebc1]

** (gnome-screensaver:3469): WARNING **: screensaver already running in this session
Failure: Module initalization failed
evolution-alarm-notify-Message: Setting timeout for 30277 1273899600 1273869323
evolution-alarm-notify-Message:  Sat May 15 00:00:00 2010

evolution-alarm-notify-Message:  Fri May 14 15:35:23 2010


(evolution-alarm-notify:3488): evolution-alarm-notify-WARNING **: Could not create the alarm notify service factory, maybe it's already running...
  
** (update-notifier:3516): WARNING **: already running?

```

---

### Post by db_asher on 2010-05-15
Thanks for the post.   Bootup Manager did the trick, for me.
Launched and clicked on Advanced settings and selected the Services tab.   
Enabled gdm and dbus, applied and restarted.
No issues now with browsers, control of application windows, display desktop...

---

### Post by DrMeers on 2010-05-20
I had the same problem, but wanted to get to the root of it rather than patching over. 

I tracked down the source of the [FONT="Courier New"]gnome-session[<...>]: WARNING: Could not launch application '<...>.desktop': Unable to start application: Failed to execute child process "<...>" (No such file or directory)[/FONT] errors.

Those [FONT="Courier New"].desktop[/FONT] files are most likely in [FONT="Courier New"]~/.config/gnome-session/saved-session[/FONT], from a previously saved session (before upgrading to Lucid?). They should be removed (or the whole directory).

Just thought I'd post for the benefit of anyone else who came across this.

---

### Post by DeltaFlight on 2010-05-28
> **DrMeers said:**
> I had the same problem, but wanted to get to the root of it rather than patching over. 

I tracked down the source of the [FONT=Courier New]gnome-session[<...>]: WARNING: Could not launch application '<...>.desktop': Unable to start application: Failed to execute child process "<...>" (No such file or directory)[/FONT] errors.

Those [FONT=Courier New].desktop[/FONT] files are most likely in [FONT=Courier New]~/.config/gnome-session/saved-session[/FONT], from a previously saved session (before upgrading to Lucid?). They should be removed (or the whole directory).

Just thought I'd post for the benefit of anyone else who came across this.

Thank you, I had the same problem and deleting files in saved-session helped me.

---

