---
title: "auto-logout on &quot;Enter&quot;"
date: 2010-03-09
forum: General Help
---

### Post by cong06 on 2010-03-09
Soon after I installed synergy and set up conky and devilspie, I started having problems with the machine loging out automatically.

As soon as I turn the computer on, it auto-logs in, and when I press enter (it seems it works for anything) the machine logs out. After logging back in it's fine however.

/var/log/syslog output:
```

Mar  9 09:08:04 kimende-s Synergy 1.3.1: FATAL: CXWindowsScreen.cpp,1597: X display has unexpectedly disconnected
Mar  9 09:08:04 kimende-s gdm[7271]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Mar  9 09:08:04 kimende-s console-kit-daemon[7092]: WARNING: Unable to activate console: No such device or address
Mar  9 09:08:11 kimende-s pulseaudio[8646]: pid.c: Stale PID file, overwriting.
Mar  9 09:08:11 kimende-s pulseaudio[8646]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Mar  9 09:08:11 kimende-s pulseaudio[8646]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Mar  9 09:08:12 kimende-s Synergy 1.3.1: NOTE: synergys.cpp,500: started server
Mar  9 09:08:12 kimende-s x-session-manager[8483]: WARNING: Could not launch application 'bluetooth-applet.desktop': Unable to start application: Failed to execute child process "bluetooth-applet" (No such file or directory)

```
(Of course there was log more output, but this is the only thing that seems related. Everything else is about "named" and "dnsmasq")

---

### Post by G-Fru on 2010-03-10
not really sure what i'm looking for in the log file, i'll post a copy shortly, but try something for me. Disable automatic login and restart your machine, at the login screen select the user and then click in the password box and type the number 2. when i do this i get booted back to the login screen again, after that pressing 2 doesn't do anything.

what sort of messages am i looking for in the log?

---

### Post by cong06 on 2010-03-26
I noticed it doesn't happen until my gnome-terminal loads.

The gnome-terminal profile in question is altered by devilspie so that the boarder is gone and it is basically merged with my desktop.

I'm switching over to tilda. We'll see if that fixes the problem.

---

### Post by cong06 on 2010-03-30
I thought it might have something to do with conky, but it seems that it's connected to my terminal some how.

The logout doesn't happen until I get a terminal up. Before it was Gnome-terminal + devilspie, now it's tilda.

---

