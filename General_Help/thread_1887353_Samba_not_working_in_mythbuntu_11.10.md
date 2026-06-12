---
title: "Samba not working in mythbuntu 11.10"
date: 2011-11-26
forum: General Help
---

### Post by dulciepercy on 2011-11-26
Hi
Just updated to 11.10 and samba does not seem to be working.  Usually mythbuntu installs it, then I install Boxee and it just finds everything for me.  I used this to work out how to find stuff through thunar (after unsuccesful search on inet).

Anyway on latest install nothing is found over the network.  Samba is running as Boxee finds things on this computer.

While writing this I just realised mythweb does not work from another computer on the network.  So it's probably a network thing and not a Samba thing.

I have no idea what to do except downgrade.  Any other ideas Please?

thanks

---

### Post by raja.genupula on 2011-11-26
if you launch from terminal , any errors are you getting ?

---

### Post by bab1 on 2011-11-27
> Just updated to 11.10 and samba does not seem to be working.


Maybe some of the Samba components aren't initializing.  You can see both the **smbd (2) ** and the **nmbd (1)** processes by running this from the CLI ```
pgrep -l mbd
```  If it is working correctly you should see something like this```
1000 smbd
1032 nmbd
1051 smbd

```

---

### Post by dulciepercy on 2011-11-28
Hi.
Thanks for the replies.  I did an update, turned samba on and off, turned computer on and off a few times.  And tonight it works!

the pgrep -l mbd  now shows as you suggested.  If it breaks again I'll come back:P

---

