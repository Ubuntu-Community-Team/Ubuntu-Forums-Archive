---
title: "Revert Terminal Command (probably easy)"
date: 2010-06-03
forum: General Help
---

### Post by nevercroft on 2010-06-03
When I log out, the "Appearance Preference" window comes up. This started happening after I was following some tutorial about how to change the login screen and I copied/pasted a line of code into a terminal and ran it. 

This is the command:

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

Could someone help me revert that command so that the apperance properties screen does not come up at login?

---

### Post by nevercroft on 2010-06-03
bump

Anyone?

---

### Post by nevercroft on 2010-06-04
Shameful re-bump. 

It can't be that hard can it? Isn't there anyone who knows how to reverse this terminal command?

---

### Post by robvas on 2010-06-04
> **nevercroft said:**
> When I log out, the "Appearance Preference" window comes up. This started happening after I was following some tutorial about how to change the login screen and I copied/pasted a line of code into a terminal and ran it. 

This is the command:

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```Could someone help me revert that command so that the apperance properties screen does not come up at login?

That line isn't causing the issue, at least not on my system. I'm trying to duplicate what you have, I get the appearance box once, but not when I logout or restart.

Post the whole script you were following. Also, what version of Ubuntu are you using?

---

### Post by nevercroft on 2010-06-04
10.04, and thats the only command I used. 

Heres the page I got that from:
[http://ubuntuforums.org/showthread.php?t=10223](http://ubuntuforums.org/showthread.php?t=10223)

scroll down to the bottom theres a post with that code in it. 

That's all I've done. If it isn't persistent on yours I have no idea why its affecting my system like this.

---

