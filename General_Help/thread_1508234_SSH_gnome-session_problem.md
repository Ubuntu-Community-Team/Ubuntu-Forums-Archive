---
title: "SSH gnome-session problem"
date: 2010-06-12
forum: General Help
---

### Post by C4rlos on 2010-06-12
Ok so this is my first post!  :p yay!
Beleve me i tried to avoid it .. but here it is:

I've got two ubuntu machines and i want to connect via ssh into a existing gnome session.(or a new one if that is possible) 
VNC works fine(well slow and unresponsive) but when trying ssh i get problems.
After som trial and error(some permissions on host, i did _sudo_ startx and screwed up) i logged in and could start xterm. Anyway now i want to use gnome, so i wrote "gnome-session" - something i read would work but i got ALOT of errors.
```
gnome-session[6094]: WARNING: Unable to find provider 'nautilus' of required component 'filemanager'

** (gnome-settings-daemon:6104): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:6104): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.

** (gnome-settings-daemon:6104): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:6104): WARNING **: Failed to connect context: Connection refused
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
gnome-session[6094]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
gnome-session[6094]: WARNING: Could not launch application 'gnome-panel.desktop': Unable to start application: Failed to execute child process "gnome-panel" (No such file or directory)
gnome-session[6094]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory)
gnome-session[6094]: WARNING: Could not launch application 'vino-server.desktop': Unable to start application: Failed to execute child process "/usr/lib/vino/vino-server" (No such file or directory)
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Failed to play sound: Not available

(polkit-gnome-authentication-agent-1:6112): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:6112): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Unable to find a synaptics device.

** (gnome-settings-daemon:6104): WARNING **: Grab failed for some keys, another application may already have access the them.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory

** (gnome-settings-daemon:6104): WARNING **: Clipboard manager is already running.
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory
Window manager warning: Screen 0 on display "localhost:10.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Failed to read saved session file /home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms: Failed to open file '/home/cwb/.config/metacity/sessions/10f0169da12c34862127637057219985600000060940026.ms': No such file or directory

```

I don't realy know if this is the way to go. I just want to connect to the host and remote control it via ssh in gnome. I did this with windows 7 --> Ubuntu with xming though i could only create a new session thus when disconnecting it would stop everything i had running.

/etc/ssh/sshd_config  : X11Forwarding yes 

I tried: "gnome-session --replace" witch seems to be totaly wrong.


Im a geek but not a linux geek , so i hope someone can help (started using Ubuntu a couple of weeks ago)

---

### Post by dryliketoast on 2010-07-29
think it's possible you may be getting confused (or me!) but from what it sounds like, you're trying to run a secure VNC session piped through SSH?

If so, that is more than possible. SSH can be used as a tunnel to the host (port to port), you can then VNC to the localhost : port on client, which is then routed to the server through the SSH tunnel

Note: SSH is CLI only. If you have 2 linux boxes, it is possible to use SSH X forwarding - which will open remote programs on the client machine. Both server & client need to be running X windows tho. This wouldn't work with Win7 as client for example.

hope this helps(!)

welcome to the world of linux :)

---

