---
title: "Does iptables reset itself after reboot?"
date: 2009-10-09
forum: General Help
---

### Post by viking_maniac on 2009-10-09
I was messing around in iptables this night using the terminal, and apparently _I messed it up_ because I suddenly couldn't access internet anymore. LOL.

*"Well, that was it!"*, I thought.

But every time I restart Ubuntu, everything works well again! :D

Is this a kind of noob-insurance built in, or what? :p
Out of curiosity, how do you make rules stick? (Not like I want that to happen, lol!)

---

### Post by CharlesA on 2009-10-09
Unless you set it to apply on boot, they'll reset after a restart.

I can't recall off the top of my head which file you'd put them in tho. (probably something to do with /etc/init.d though.)

---

### Post by diesch on 2009-10-09
The iptables settings aren't automatically saved. You can use 
```
iptables-save > /etc/iptablesrc
```
to save them and 
```
iptables-restore < /etc/iptablesrc
```
to restore your saved settings (you can user any other filename instead of /etc/iptablesrc).

---

### Post by mkarl on 2009-10-09
If you mess up iptables you can avoid having to restart by doing 'iptables --flush' which normally deletes all the current rules.

Karl :)

---

