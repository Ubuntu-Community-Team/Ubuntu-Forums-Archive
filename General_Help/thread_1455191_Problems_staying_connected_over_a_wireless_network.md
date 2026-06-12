---
title: "Problems staying connected over a wireless network (Compaq CQ61))"
date: 2010-04-15
forum: General Help
---

### Post by ninjaaron on 2010-04-15
I've been using Ubuntu for a little more than a year now, but my old computer just broke, and I recently installed Ubuntu(64 bit version) on a new machine, a Compaq Presario CQ61.

Anyway, after the computer has been on for a little while (usually not more than thirty minutes, sometimes much less, occasionally much longer), I no longer get service from the router. I remain connected, simply no service. Sometimes it comes back for a little while if I disconnect and reconnect. Sometimes not. It usually comes back if I turn off the computer, but not for too long. The other people on the network do not experience this, nor do I when using the Windows partition of the same machine (as I am at the moment). It is infuriating to no end.

On the other hand, I guess there isn't much better security than not being able to get online 8^).

Thanks,
Aaron

P.S. I am graciously being allowed to use someone else's service, and I can't exactly run around making demands about network protocols or things like that. I need a solution from within the OS, especially since the network isn't giving anyone else problems with the current setting.

---

### Post by linden940 on 2010-04-15
sounds like the hardware MAY not be supported in Ubuntu 

something to check

---

### Post by ninjaaron on 2010-04-15
Thanks. That seems to have been the issue. My card was an Atheros AR9285. Apparently it's a normal problem. I installed some "backport modules," whatever those are, and it appears to have fixed the problem (though I haven't been on very long, the signal strength is much improved, and smooth sailing thus far).

Here's a link to the thread with the fix:
[http://ubuntuforums.org/showthread.php?t=1341618]("http://ubuntuforums.org/showthread.php?t=1341618")

---

