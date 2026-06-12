---
title: "Tightvncserver crashes when trying to run gnome-session"
date: 2010-05-12
forum: General Help
---

### Post by adante on 2010-05-12
My system is 9.10 ubuntu 64. Tightvnc used to run fine on 9.04.

When I run tightvncserver and connect to it, it crashes after I try to start gnome-session.

At the moment I use an xstartup script that just starts xterm


```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
#gnome-session
xterm

```


Once vncserver starts I try to run gnome-session

```
gnome-session 2>&1 | tee gnome.log
```

Things start coming up but before it finishes loading it crashes.

gnome.log says:

```

Xlib:  extension "RANDR" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
gnome-session[30747]: WARNING: GSIdleMonitor: IDLETIME counter not found
gnome-session[30747]: WARNING: Unable to determine session: Unable to lookup session information for process '30747'
Xlib:  extension "RANDR" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
gnome-session[30747]: WARNING: Could not launch application 'at-spi-registryd-wrapper.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-session/helpers/at-spi-registryd-wrapper" (No such file or directory)
GNOME_KEYRING_SOCKET=/tmp/keyring-vF04kv/socket
SSH_AUTH_SOCK=/tmp/keyring-vF04kv/socket.ssh
GNOME_KEYRING_PID=30763
Xlib:  extension "RANDR" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".

** (gnome-settings-daemon:30757): WARNING **: Unable to start xrandr manager: RANDR extension is not present
Xlib:  extension "RANDR" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "RANDR" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
** (<unknown>:30760): DEBUG: Client registered with session manager: /org/gnome/SessionManager/Client2
Checking for Xgl: Xlib:  extension "XVideo" missing on display ":6.0".
xvinfo: No X-Video Extension on :6.0
not present. 

** (gnome-settings-daemon:30757): WARNING **: XKB extension not available

** (gnome-settings-daemon:30757): WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings
Xlib:  extension "XInputExtension" missing on display ":6.0".
Unable to find a synaptics device.
Xlib:  extension "XInputExtension" missing on display ":6.0".
Xlib:  extension "XInputExtension" missing on display ":6.0".
Xlib:  extension "XInputExtension" missing on display ":6.0".
Xlib:  extension "XInputExtension" missing on display ":6.0".
Xlib:  extension "XInputExtension" missing on display ":6.0".
Xlib:  extension "XInputExtension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
egrep: /var/log/Xorg.0.log: No such file or directory
egrep: /var/log/Xorg.0.log: No such file or directory
egrep: /var/log/Xorg.0.log: No such file or directory
egrep: /var/log/Xorg.0.log: No such file or directory
egrep: /var/log/Xorg.0.log: No such file or directory
egrep: /var/log/Xorg.0.log: No such file or directory
egrep: /var/log/Xorg.0.log: No such file or directory
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Xlib:  extension "RANDR" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Window manager warning: Failed to read saved session file /home/USERREDACTED/.config/metacity/sessions/105c45025ed7cc7bb127372198412791200000307470026.ms: Failed to open file '/home/USERREDACTED/.config/metacity/sessions/105c45025ed7cc7bb127372198412791200000307470026.ms': No such file or directory
Window manager warning: Log level 32: could not find XKB extension.
Xlib:  extension "RANDR" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "RANDR" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "RANDR" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "RANDR" missing on display ":6.0".
Xlib:  extension "RANDR" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Xlib:  extension "Generic Event Extension" missing on display ":6.0".
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':6.0'.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :6.0.
Cannot open display: 
Run 'bluetooth-applet --help' to see a full list of available command line options.

```

How can I run gnome-session?

---

