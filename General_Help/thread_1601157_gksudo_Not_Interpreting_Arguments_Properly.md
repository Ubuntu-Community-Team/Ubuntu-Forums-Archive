---
title: "gksudo Not Interpreting Arguments Properly?"
date: 2010-10-19
forum: General Help
---

### Post by silverhammermba on 2010-10-19
I'm trying to run the command
```
$fspc -t -l ~/.fspc/fspc.ini
```
with gksudo. The problem is that if I just do
```
$gksudo fspc -t -l ~/.fspc/fspc.ini
```
gksudo just runs fspc without any of its arguments (which brings up my touchpad configuration GUI, rather than loading the touchpad configuration from the file). I'm pretty sure what's happening is that it's reading the arguments for fspc as the arguments for gksudo.

If I run
```
$gksudo fspc -d -t -l ~/.fspc/fspc.ini
```
I get the output
```
No ask_pass set, using default!
xauth: /tmp/libgksu-pkT3Nc/.Xauthority
STARTUP_ID: gksudo/fspc '|home|   |.fspc|fspc.ini'/3758-0-epsilon_TIME1074670
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: fspc
cmd[9]: /home/   /.fspc/fspc.ini
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.
xauth: /tmp/libgksu-pkT3Nc/.Xauthority
xauth_env: /var/run/gdm/auth-for-max-Qz3csu/database
dir: /tmp/libgksu-pkT3Nc

```
Which is the debug output for gksudo, not fspc!

How do I get it to interpret the args the way I want?

---

### Post by kerry_s on 2010-10-19
gksudo "fspc -t -l ~/.fspc/fspc.ini"

---

