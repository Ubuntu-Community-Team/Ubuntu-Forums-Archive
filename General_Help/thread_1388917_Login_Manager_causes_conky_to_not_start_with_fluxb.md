---
title: "Login Manager causes conky to not start with fluxbox"
date: 2010-01-23
forum: General Help
---

### Post by moforilla on 2010-01-23
I recently upgraded from 9.04 to 9.10 and I have noticed an increase in loading time when logging in.

What use to take less then 1 sec is now taking 3-4. It sometimes is able to start conky but most of the time it doesn't. When I manual run it after login in it has no problems starting.

When I start a session with 9.04 I noticed it would go straight to fluxbox it would then take a few seconds to load conky and pidgin. When starting a session with 9.10 the loading seems to happen before the login manager passes control to fluxbox. When the login manager is finished pidgin is signed and ready, there is no more loading to be done.

Would removing the login manager and starting a session from the terminal be advisable? I only use fluxbox.

---

### Post by VCoolio on 2010-01-23
Delay conky to fit your wm loading time. Use a script and call that at startup instead of conky:

```
#!/bin/sh
sleep 10 && conky
```

---

### Post by moforilla on 2010-01-23
Thank you for the suggestion Vcoolio but I'm stilling getting the same problem. The only difference is that now gdm waits 10 seconds before loading and no conky is loaded.

I created a script called startconky.sh and put that command in it. I then replaced the line in the /home/nraic/.fluxbox/startup file to call that command in stead of conky.

```
/home/nraic/.fluxbox/startup

#exec /usr/bin/nm-applet&
exec /usr/bin/pidgin&
exec /home/nraic/startconky.sh&

nitrogen --restore &

#eval `cat $HOME/.fehbg` &


# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

```

Is this what you meant when you said to add my script to the startup?

---

### Post by VCoolio on 2010-01-24
exactly, I meant the second way; so did that work?

---

### Post by moforilla on 2010-01-25
No, this has not worked. I now have to wait 13 seconds and conky still doesn't started.

Should I report this as a bug? I don't mind removing gdm but I'm not sure if that is what my login manager is. I tried finding it using a system configuration tool and gdm was not enabled service.

---

### Post by moforilla on 2010-01-25
I think I found the problem. I was incorrectly invoking commands from my .fluxbox/startup file.

I should not have been using exec before each program but only when calling fluxbox last.

---

