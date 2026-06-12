---
title: "LightDM won't log in like in &quot;Precise known workarounds&quot; except they don't work."
date: 2012-05-25
forum: General Help
---

### Post by J V on 2012-05-25
Logging into xubuntu normally through lightdm nothing happens until I switch to a TTY and log in there, after a while lightdm will respond and continue with the boot.

Moving wallpaper outside of the encrypted home directory did nothing (Which is sort of to be expected since you'd need the directory decrypted to know which wallpaper to use anyway)

This is the LightDM log:

There is a [bug report](https://bugs.launchpad.net/lightdm/+bug/870685) that has been stalled for days, and the workaround for this bug posted in "Precise workarounds" doesn't work...

```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=1139
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.00s] DEBUG: X server :0 will replace Plymouth
[+0.02s] DEBUG: Using VT 7
[+0.02s] DEBUG: Activating VT 7
[+0.02s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.02s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.02s] DEBUG: Launching X Server
[+0.02s] DEBUG: Launching process 1168: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.02s] DEBUG: Waiting for ready signal from X server :0
[+0.02s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.02s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+1.09s] DEBUG: Got signal 10 from process 1168
[+1.09s] DEBUG: Got signal from X server :0
[+1.09s] DEBUG: Stopping Plymouth, X server is ready
[+1.11s] DEBUG: Connecting to XServer :0
[+1.11s] DEBUG: Starting greeter
[+1.11s] DEBUG: Started session 1405 with service 'lightdm', username 'lightdm'
[+1.13s] DEBUG: Session 1405 authentication complete with return value 0: Success
[+1.13s] DEBUG: Greeter authorized
[+1.13s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+1.13s] DEBUG: Session 1405 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+1.16s] DEBUG: Greeter connected version=1.2.1
[+1.16s] DEBUG: Greeter connected, display is ready
[+1.16s] DEBUG: New display ready, switching to it
[+1.16s] DEBUG: Activating VT 7
[+1.31s] DEBUG: Greeter start authentication for j
[+1.31s] DEBUG: Started session 1686 with service 'lightdm', username 'j'
[+1.31s] DEBUG: Session 1686 got 1 message(s) from PAM
[+1.31s] DEBUG: Prompt greeter with 1 message(s)
[+24.47s] DEBUG: Continue authentication
[+24.88s] DEBUG: Session 1686 authentication complete with return value 0: Success
[+24.88s] DEBUG: Authenticate result for user j: Success
[+24.89s] DEBUG: User j authorized
[+24.89s] DEBUG: Greeter sets language en_US
[+24.89s] WARNING: Could not call SetLanguage: GDBus.Error:org.freedesktop.Accounts.Error.Failed: not access to HOME yet so language not saved
[+24.89s] DEBUG: Greeter requests session xubuntu
[+24.89s] DEBUG: Using session xubuntu
[+24.89s] DEBUG: Stopping greeter
[+24.89s] DEBUG: Session 1405: Sending SIGTERM
[+24.90s] DEBUG: Session 1405 exited with return value 0
[+24.90s] DEBUG: Greeter quit
[+49.93s] WARNING: Could not call SetXSession: Timeout was reached
[+74.95s] WARNING: Could not call FindUserByName: Timeout was reached
[+74.95s] DEBUG: Dropping privileges to uid 1000
[+74.97s] DEBUG: Restoring privileges
[+100.00s] WARNING: Could not call FindUserByName: Timeout was reached
[+100.00s] DEBUG: Dropping privileges to uid 1000
[+100.00s] DEBUG: Writing /home/j/.dmrc
[+100.04s] DEBUG: Restoring privileges
[+100.05s] DEBUG: Starting session xubuntu as user j
[+100.05s] DEBUG: Session 1686 running command /usr/sbin/lightdm-session startxfce4
[+100.08s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+100.08s] DEBUG: Greeter closed communication channel
```

---

### Post by rai4shu2 on 2012-05-25
Slow login is a ship that has sailed a few times in this thread:

[http://ubuntuforums.org/showthread.php?t=1970326](http://ubuntuforums.org/showthread.php?t=1970326)

see [post #15]("http://ubuntuforums.org/showpost.php?p=11918449&postcount=15")

---

### Post by J V on 2012-05-25
Awesome thanks I'll update the "Known issues and workarounds" thread :)

---

### Post by test666 on 2012-06-06
> **J V said:**
> Awesome thanks I'll update the "Known issues and workarounds" thread :)

Sorry to ask, but can you put a link to this thread? Thank you.

---

