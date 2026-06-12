---
title: "Flash Audio Issue"
date: 2011-12-03
forum: General Help
---

### Post by Jaybyrrd on 2011-12-03
Ok so I am currently having an issue with Flash having an audio delay. I have seen guides to fixing it using Firefox, however I am using Chromium. Any suggestions? Thanks!

---

### Post by oldtimer7777 on 2011-12-03
> **Jaybyrrd said:**
> Ok so I am currently having an issue with Flash having an audio delay. I have seen guides to fixing it using Firefox, however I am using Chromium. Any suggestions? Thanks!

Did you install it from the PPAs?

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It is about 1/3rd the way down the list.

Try using Chrome instead since it has its own flash plugin and doesn't use the Adobe Flash plugin used by Chromium or Firefox.

Install Chrome from the PPA in the link above too.  Piece of cake.

Also if nothing else helps, try using Flash Aid plugin for Firefox, and it will update your flash plugin for Chromium and Firefox to the Stable version.

---

### Post by Jaybyrrd on 2011-12-03
Neither of those resulted in a fix. Thanks though. :(

---

### Post by oldtimer7777 on 2011-12-03
> **Jaybyrrd said:**
> Neither of those resulted in a fix. Thanks though. :(

Try switching to the Ubuntu 2d session during login.

---

### Post by Jaybyrrd on 2011-12-03
I am using Gnome, I just went away from Unity. Does that count?

---

### Post by oldtimer7777 on 2011-12-03
> **Jaybyrrd said:**
> I am using Gnome, I just went away from Unity. Does that count?

do you have Compiz installed? If so uninstall it.

check additional drivers..

sudo jockey-gtk

Do you see anything that still needs to be installed there?

---

### Post by Jaybyrrd on 2011-12-03
Yeah I do.

---

### Post by oldtimer7777 on 2011-12-03
> **Jaybyrrd said:**
> Yeah I do.

Remove that fancy window dressing nonsense and compiz. Just uninstall it from synaptic package manager.

sudo apt-get install synaptic
sudo synaptic

Afterwards, reboot and power cycle your system.

Next you need to clean your system:

sudo apt-get install bleachbit
sudo bleachbit

---

### Post by Jaybyrrd on 2011-12-03
Alright give me a minute, luckily I already have synaptic, let me just make this happen real quick, I will edit with an update. However I don't think it has anything to do with compiz as this is an audio issue..

Problem still exists.

---

