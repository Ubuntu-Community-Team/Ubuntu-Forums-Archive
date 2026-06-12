---
title: "How to reset network-manager?"
date: 2009-11-01
forum: General Help
---

### Post by varelasaraiva on 2009-11-01
Hi everyone,

I'm sorry if something similar was already posted but I could not find it.

For some reason my network-manager stopped connecting to my home wireless lan. It connects everywhere else except here. I tried for example listening to syslog to see if I could get any clue but got nothing. Tried removing completely network-manager-gnome and wpa-supplicant but again to no avail.

I remembered to try the Karmic live image and it connects in less than a second at startup, therefore I can conclude there is something wrong with the configuration of either network-manager, wpa-supplicant or gnome-keyring since a vanilla installation works just fine.

It's not the best time to do a fresh install - it's a production machine with lots of tweaks and workarounds - so I was wondering if there is any way to wipe clean network-manager and related stuff. Removing completely those packages doesn't lose for example the wep, wpa keys for all the networks I use so I suppose it keeps some residual stuff.

I'm happy to check individual conf files in /etc for clues but I need pointers.

No, it didn't stop working after upgrading to Karmic.

Many thanks in advance.

---

### Post by picante on 2010-08-08
This is exactly the same problem I have. I tried reinstalling Ubuntu (Lucid) but the problem persists exactly as before.

---

