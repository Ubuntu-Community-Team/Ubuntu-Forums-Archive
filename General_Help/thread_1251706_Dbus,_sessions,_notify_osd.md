---
title: "Dbus, sessions, notify osd"
date: 2009-08-28
forum: General Help
---

### Post by SoftwareExplorer on 2009-08-28
Hi, I'm trying to figure out how to send notify-osd messages to a user when they are at the physical computer and I'm ssh'ed in. I know notify-osd uses dbus, but I don't know what command to use. I think this would require sending messages to other sessions or whatever they are called.
I already talked about this in [this thread]("http://ubuntuforums.org/showthread.php?t=1203659"), but I was suggested that I start another thread with dbus in the title.

Thank in advance!

---

### Post by SoftwareExplorer on 2009-10-04
I'm still interested if anyone knows how to do this.

---

### Post by cn28h on 2009-10-18
The trick is getting the correct value into the DBUS_SESSION_BUS_ADDRESS environment variable.  Once that's set you should be able to communicate on that session bus (as that user).  To find this variable, you can look in ~target-user/.dbus/session-bus/. There should be a long id name there, and inside of that file you should find this variable.

export this variable in your shell, then run something like:

```

sudo -E -u target-user <msg_command>

```
and poof, assuming notify-osd is running, the user should get a notification.

---

### Post by SoftwareExplorer on 2009-10-20
There was multiple ones of those files, so after looking at one, I did this to get them all listed nicly
```
cat dd6957df5efe681b59e1932449c3326b-0 dd6957df5efe681b59e1932449c3326b-20 dd6957df5efe681b59e1932449c3326b-21 dd6957df5efe681b59e1932449c3326b-22 dd6957df5efe681b59e1932449c3326b-23| grep DBUS_SESSION_BUS_ADDRESS=
```
and got
```
957df5efe681b59e1932449c3326b-23| grep DBUS_SESSION_BUS_ADDRESS=
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-8KyO1NHyAt,guid=ba20a5c3163f50aa3a6d5dce4ad4d66a
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-8pYo5UEzRd,guid=1e6ce7b3132bc1f8de1748794adb5515
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-s9NXRkjFfT,guid=7ff71716d43efb13fdf2ac114acaae40
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-L7bDCFzUFO,guid=c25e80873d5bbe64e755004a4aaa8148
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-iESez9y7LJ,guid=84be9bf3a7faa715f0ebaf4b4a6934dd

```
I tried each one like this
```
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-L7bDCFzUFO,guid=c25e80873d5bbe64e755004a4aaa8148                                    (10-19 21:55:30)
[bjorn@bjorn-desktop:.dbus/session-bus]$ sudo -E -u marta notify-send "HI!"
```
and got
```
libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
```
Thanks for the help.

---

### Post by cn28h on 2009-10-20
I believe you want to be matching the uuid to the one in /var/lib/dbus/machine-id (it will change each time you reboot).

Also, assuming you are using bash, simply setting the variable won't make it visible in the environment -- you must also export it.

so,

```

export DBUS_SESSION_BUS_ADDRESS=...

```

for example.

---

### Post by SoftwareExplorer on 2009-10-20
Thanks, it worked. The exporting was my problem. The files in /home/username/.dbus/session-bus are all named </var/lib/dbus/machine-id>-anumber. After trial and error, I find the right one and it works! Thanks.

---

