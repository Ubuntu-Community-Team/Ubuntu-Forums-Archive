---
title: "syndaemon running by default on my system - how do I modify the launch command"
date: 2009-11-20
forum: General Help
---

### Post by mattengstrom on 2009-11-20
Syndaemon is running by default on my system for all users, and I'd like to modify its options, but I can't figure out what's launching it.
```

ps -ef | grep syndaemon
```

gives me

```
matt      2378     1  0 10:23 ?        00:00:00 syndaemon -i 0.5 -k
```

and I want to add some extra flags to that, and change the 0.5 interval.  There's nothing in my startup apps that seems to refer to this.  Any suggestions on where else to look?

---

### Post by MaxIBoy on 2009-11-20
Look in /etc/init.d. This is where your initscripts are. Should be fairly straightforward to edit the launch command, but BACK IT UP JUST IN CASE! Also, automatic updates now warn that the file is modified and if it needs to be updated. The best way to update is to save off your custom version, let it update, then merge in your customizations to the new one. This doesn't come up very often, so for me its not usually a problem.

---

### Post by FokkerCharlie on 2009-11-26
I'm seeing this- and there's nowt in /etc/init.d that looks like syndaemon to me.  Did you find what you were looking for?  Could you post what you did?

Ta!

Charlie

Edit:  Scrub that!  Go to System > Prefs > Mouse > Touchpad, untick 'Disable touchpad when typing', then put what you really want in the startup apps thingie.

---

