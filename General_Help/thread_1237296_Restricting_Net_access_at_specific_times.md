---
title: "Restricting Net access at specific times"
date: 2009-08-11
forum: General Help
---

### Post by rolnics on 2009-08-11
This probably could go in a number of different areas, so feel free to move.

I would like to be able to stop internet access to our laptop at a specific time every day. The reason being is my son gets carried away with games on the net and doesn't want to go to bed. The amount of time doesn't need to be more than 15mins or less.

Is there a way of doing this and how, an added twist is at the moment the laptop isn't on a static IP address and I'm not using wireless, but this might change.

---

### Post by credobyte on 2009-08-11
The easiest way would be to create a cron job.

22:00 ( 10:00 PM ):
```
#!/bin/bash
sudo ifdown eth0
```8:00 ( 8:00 AM ):
```
#!/bin/bash
sudo ifup eth0
```And save the second one as a backup so you could launch it at any time to get your connection up and running again.

---

### Post by ZizzerZuz on 2009-08-11
I have found that I can control this via my router using MAC addresses.  I run dd-wrt on a linksys.  If, for some reason you need Internet on that PC, log in to the router and allow it, I can have several saved access control lists that I can choose between.

---

### Post by gibbylinks on 2009-08-11
> **ZizzerZuz said:**
> I have found that I can control this via my router using MAC addresses.  I run dd-wrt on a linksys. 

I also have this option on my TP-Link router. You can pick days and times when to allow access. If your using a router it would be worth looking into. :)

---

