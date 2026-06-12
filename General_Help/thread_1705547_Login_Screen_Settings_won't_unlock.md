---
title: "Login Screen Settings won't unlock"
date: 2011-03-12
forum: General Help
---

### Post by AirBiscuit on 2011-03-12
As above. I'm trying to change some login settings, but the window won't unlock. I click the button, and nothing happens. Any ideas? I'm using 10.10.

---

### Post by AirBiscuit on 2011-03-12
Bump for the day shift

---

### Post by cap10Ibraim on 2011-03-12
try the following 
first run 
```

ps -aux | grep poltik-gnome

```
you should see some thing similar to 
```

ibrahim   2406  0.0  0.0   7624   940 pts/0    S+   20:15   0:00 grep --color=auto poltik-gnome

```
if you don't 
open /usr/lib/policykit-1-gnome 
and the open the terminal and drag the .exe file to the terminal and hit enter 
try to unlock now

---

### Post by AirBiscuit on 2011-03-12
> Warning: bad ps syntax, perhaps a bogus '-'?

I guess this is the problem, then...

---

### Post by cap10Ibraim on 2011-03-12
did you run the file in /usr/lib/policykit-1-gnome ?

---

### Post by AirBiscuit on 2011-03-12
Yes, this was the response:

> (polkit-gnome-authentication-agent-1:5857): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:5857): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (polkit-gnome-authentication-agent-1:5857): WARNING **: Unable to register authentication agent: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.RegisterAuthenticationAgent() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session
Cannot register authentication agent: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.RegisterAuthenticationAgent() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for session


Thank you for the help so far, by the way! Very much appreciated.

---

