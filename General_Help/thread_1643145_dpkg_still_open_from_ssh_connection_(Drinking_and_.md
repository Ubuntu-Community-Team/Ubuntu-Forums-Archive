---
title: "dpkg still open from ssh connection (Drinking and SSHing)"
date: 2010-12-11
forum: General Help
---

### Post by earthpigg on 2010-12-11
so, i was playing with my android phone. just for kicks, i decided to run sudo apt-get update and upgrade from the bar. you know, "because i can".

then, during the upgrade, the EULA for the MS fonts came up. wouldn't you know it, no tab button on the phone and no way to select 'accept' on the ncurses dialog.

i said 'bah' and put it back in my pocket. naturally, the ssh connection shut down.

now, from sudo apt-get update...

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[chris: ~]$ ps -A | grep dpkg
19856 pts/2    00:00:02 dpkg
```

i don't want to shut down or restart with an upgrade half-complete, as that doesn't seem safe. i also don't want to kill it for the same reason.

how would i gain access to pts/2 so i can hit 'accept' and let the upgrade complete?

---

### Post by gmargo on 2010-12-12
> **earthpigg said:**
> no tab button on the phone and no way to select 'accept' on the ncurses dialog.
Does it have a Control (Ctrl) key?  Control-i is a tab.

---

### Post by wojox on 2010-12-12
I think you have to kill it. Look in /dev/pts/

It's a virtual terminal.

---

### Post by earthpigg on 2010-12-12
i killed it and ran dpkg --reconfigure -a or similar, and all is back to normal.

---

