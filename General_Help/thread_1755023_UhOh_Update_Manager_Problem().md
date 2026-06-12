---
title: "UhOh Update Manager Problem(?)"
date: 2011-05-10
forum: General Help
---

### Post by jfbooth on 2011-05-10
A few days ago I upgraded Xubuntu from 10.10 to 11.04 with Update Manager (online).  It seemed to go very well.  Today, I noticed the first 'batch' of updates for 11.04.  I (as usual) clicked on the icon, Update Manger opened listing a batch of updates.  I clicked Install, provided password, and nothing happened. No indication anything was downloading .. no drive activity .. it just sat there.  After some time, I hit cancel ...and 'got out' of Update Manager.

Now, there is no notification of updates.  Update Manager, when I 'Check for updates' tells me system is 'up to date' .. no updates available.

I am left to wonder if I am out of date, and somehow Update Manager is 'out of sync' or something.

Can anyone tell me if I am up to date or not (how to determine)?  Update Manager MIGHT be lying to me.  I mean MAYBE those updates installed .. but it did not 'look' like anything did to me.

Thank you in advance.

---

### Post by VanR on 2011-05-10
Open a terminal and type

sudo apt-get update && sudo apt-get upgrade

then your password when prompted

That will tell you if you have any updates and install them.

---

### Post by jfbooth on 2011-05-10
> **VanR said:**
> Open a terminal and type

sudo apt-get update && sudo apt-get upgrade

then your password when prompted

That will tell you if you have any updates and install them.

Thank you, Sir/Ma'am for your prompt reply.  Evidently .. all OK.  Your command seemed to do a 'scan/check' and the results are:

0 upgraded, 0 newly installed, 0 to remove, 0 not upgraded

I am concluding I am OK.  Thank you again.

---

