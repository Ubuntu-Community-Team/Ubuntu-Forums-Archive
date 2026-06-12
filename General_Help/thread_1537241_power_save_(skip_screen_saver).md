---
title: "power save (skip screen saver)"
date: 2010-07-23
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-07-23
I am trying to make a script that will skip the screen saver stage and just shut the monitor off (and not come on till the computer is touched)
```
#!/bin/sh
gnome-screensaver-command --lock
xset dpms force off
gnome-screensaver-command --inhibit
exit
```that appears to work but i want it to exit after the computer is touched again

---

### Post by ubunterooster on 2010-07-23
Make a launcher or enter it into the "run" dialog.

Any idea how to make a script skip the lock part and go straight to turning off the screen?

---

### Post by pqwoerituytrueiwoq on 2010-07-23
> **ubunterooster said:**
> Any idea how to make a script skip the lock part and go straight to turning off the screen?
delete line 2 of the script i posted and it will do that[FONT=monospace]

if you delete [/FONT]*gnome-screensaver-command --inhibit* the screen will come back on after 80 seconds
if you do not want to do that you have to use a while loop sleep 80 then turn screen off

---

### Post by ubunterooster on 2010-07-23
That works for me, thanks

---

### Post by HarmtH on 2010-08-09
gnome-screensaver-command --inhibit waits for a ^C, so that won't work, or maybe you can run in in the background with the '&' and then kill the process afterwards.

But the way I do it is to simulate user activity until the screensaver is turned off:

> sleep 1 && dbus-send --session           --dest=org.gnome.ScreenSaver           --type=method_call           --print-reply           --reply-timeout=20000           /org/gnome/ScreenSaver           org.gnome.ScreenSaver.SetActive           boolean:true && sleep 1 && xset dpms force off

while (dbus-send --session           --dest=org.gnome.ScreenSaver           --type=method_call           --print-reply           --reply-timeout=20000           /org/gnome/ScreenSaver           org.gnome.ScreenSaver.GetActive | grep true); do sleep 1; dbus-send --session           --dest=org.gnome.ScreenSaver           --type=method_call           --print-reply           --reply-timeout=20000           /org/gnome/ScreenSaver           org.gnome.ScreenSaver.SimulateUserActivity; doneThe while-loop checks every second if the screensaver is still running, and if so it pokes the screensaver. This way it won't put the monitor in blank screen mode after 80 seconds.

---

### Post by pqwoerituytrueiwoq on 2010-08-19
> **HarmtH said:**
> gnome-screensaver-command --inhibit waits for a ^C, so that won't work, or maybe you can run in in the background with the '&' and then kill the process afterwards.

But the way I do it is to simulate user activity until the screensaver is turned off:

The while-loop checks every second if the screensaver is still running, and if so it pokes the screensaver. This way it won't put the monitor in blank screen mode after 80 seconds.
looks like it is giving an error
```
method return sender=:1.56 -> dest=:1.131 reply_serial=2
   boolean true
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
   boolean true
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

---

