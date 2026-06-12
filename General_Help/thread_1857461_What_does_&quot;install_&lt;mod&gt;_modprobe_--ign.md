---
title: "What does &quot;install &lt;mod&gt; modprobe --ignore-install &lt;mod&gt;&quot; mean?"
date: 2011-10-10
forum: General Help
---

### Post by Intrepid Ibex on 2011-10-10
Upon Googling I found this line to fix my network connection from dropping with the [[COLOR="DarkSlateGray"]_r8169 driver_[/COLOR]](http://forums.fedoraforum.org/showthread.php?t=250807):
```
# turn off autonegotiation on the r8169 ethernet driver
install r8169 /sbin/modprobe --ignore-install r8169 && /usr/sbin/ethtool -s eth0 autoneg off
```

I'd just like to find out what the first part means.

Thanks.

---

### Post by Intrepid Ibex on 2011-10-11
Anybody?

---

### Post by Intrepid Ibex on 2011-10-12
Ooooh, ok, now I get it. I finally understood the man page here: _[COLOR="DarkSlateGray"][http://linux.die.net/man/5/modprobe.conf_[/COLOR]](http://linux.die.net/man/5/modprobe.conf_[/COLOR]).

So whenever
```
modprobe r8169
```
is called, instead of just probing the module this command is ran instead:
```
/sbin/modprobe --ignore-install r8169 && /usr/sbin/ethtool -s eth0 autoneg off
```
the **--ignore-install** part means to not run the same command yet again (because **modprobe r8169** is ran in the insterted command itself - this would create an infinite loop otherwise).

---

