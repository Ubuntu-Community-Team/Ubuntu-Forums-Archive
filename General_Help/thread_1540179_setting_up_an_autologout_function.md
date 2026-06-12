---
title: "setting up an autologout function"
date: 2010-07-27
forum: General Help
---

### Post by malachi1990 on 2010-07-27
I'm hoping to be able to set up ubuntu for a few people, but they need to be able to control how long the kids are on the computer.  Is there any utility that exists for linux that can handle this? 

So far, everything I've seen tries to autologout after a set period of idleness (ie the kid leaves the computer for 15 minutes and gets logged out because of that), but that's not exactly what I need (if it helps, I'm looking for something that will log you out at say 1 hr after logging in, either by starting a screensaver, or forcibly logging you out).

Thanks in advance.

---

### Post by geoffjay on 2010-07-27
Create two scripts, one with the following contents to create the timer, and another to do the logout.

$ vim schedule-logout.sh
```

#!/bin/bash
at -f /path/to/logout.sh now + 60 minutes

```
$ chmod +x schedult-logout.sh

$ vim logout.sh
```

#!/bin/bash
gnome-session-save --force-logout

```
$ chmod +x logout.sh

Now for every user that needs this go to System -> Prefereces -> Startup Applications and create a new entry for the schedule-logout.sh script.

I haven't actually tried this so can't confirm whether or not it will even work, so I'd be interested in knowing if it does as I can think of a couple of places that this could be used in my network.

---

### Post by rnerwein on 2010-07-27
hi
i don't know if this is a resolution for you. but i have .... kid's and ... boxes here. they are running windows, linux and solaris.
the only way i can handle that stuff i configured my primary router with rules ( eg. macaddress from time ... to and so on  for each mac-address with different timeslices -- works ).
i stay in germany and get a telecom router VT..... 
have a look at your router i think there is a way to do that too.
but this is only a solution if you get more than one box ( mac adress ).
another hint can be the --> /etc/securirty/limits.conf with the option: cpu - max CPU time (MIN)
but i think that's to hard :-)
ciao

---

