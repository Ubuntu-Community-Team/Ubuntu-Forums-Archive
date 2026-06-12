---
title: "upgrading ubuntu..."
date: 2006-04-23
forum: General Help
---

### Post by lonelypauly on 2006-04-23
what happens to all of us 5.10 users when dapper drake is released?  how does this work exactly? are we upgraded through automatic updates, or is this an entirely new OS that has to be installed over the old one?

---

### Post by PriceChild on 2006-04-23
We will simply update our sources list, and do...
```
apt-get update
apt-get dist-upgrade
```
Quite simple :) ......... In theory :) You may have troubles if you've messed with your system enough :)

Personally, i'm going to backup all my data and do a nice reinstall :) Worked better for me on the Breezy upgrade :)

---

### Post by jobezone on 2006-04-23
[QUOTE=lonelypauly]what happens to all of us 5.10 users when dapper drake is released?  how does this work exactly? are we upgraded through automatic updates, or is this an entirely new OS that has to be installed over the old one?[/QUOTE]
When Dapper is released, update-manager will inform you, and ask if you want to upgrade to it.

---

### Post by sinkxdie on 2006-04-23
Wait, so all we need to do is install an update and then it will be updated?
We won't have to reinstall any OS or something?

---

### Post by aysiu on 2006-04-23
[QUOTE=jobezone]When Dapper is released, update-manager will inform you, and ask if you want to upgrade to it.[/QUOTE] I don't believe this is true, actually. This is a feature that's supposed to be implemented for Dapper (that will prompt you to upgrade to Edgy Eft), but I think to upgrade from Breezy to Dapper, you actually need to do [this](http://www.psychocats.net/ubuntu/dapper).

[quote=sinkxdie]Wait, so all we need to do is install an update and then it will be updated?
We won't have to reinstall any OS or something?[/quote] Theoretically, you can just upgrade to Dapper from Breezy. Sometimes, especially if you don't follow the directions I link to above, there's breakage. That breakage *can* be fixed (usually something with either the X server or locales), but people usually just go for a clean reinstall. I suspect, particularly with Dapper, that people will just reinstall because they want to see this new graphical "Espresso Installer" in action.

If you have a separate /home partition, you can reinstall without losing any important data or preferences. You may just have to reinstall a few programs.

---

### Post by sinkxdie on 2006-04-23
O thanks, but is the beta stable?

---

### Post by aysiu on 2006-04-23
[QUOTE=sinkxdie]O thanks, but is the beta stable?[/QUOTE] If you use Ubuntu to get work done in a timely fashion and **cannot** afford to have downtime--even for one day--do not install Dapper. Breakage is not necessarily to be expected, but if it does happen, don't complain.

That said, I've been using Dapper for a couple of weeks now, and I've had no *real* problems. Every now and then (especially in Gnome), an application has crashed, but then I just relaunch it.

---

### Post by lonelypauly on 2006-04-23
ok, so another question...i have my Nvidia twinview setup exactly the way i want it...had alot of help from ilya with my config file...i just back up my config file and copy it over the default config assuming i do a fresh install of dapper?

what is the main difference between the KDE and Gnome desktops anyway?
is Gnome better for a noob like myself?

---

### Post by jobezone on 2006-04-23
[QUOTE=aysiu]I don't believe this is true, actually. This is a feature that's supposed to be implemented for Dapper (that will prompt you to upgrade to Edgy Eft), but I think to upgrade from Breezy to Dapper, you actually need to do [this](http://www.psychocats.net/ubuntu/dapper).[/QUOTE]
I remember seeing this feature mentioned in the changelog of update-manager (I thought) when upgrading a breezy system. I've now searched for that changelog and I can't find it, so I'm not sure if the changelog I read belonged to another package, or I just misread it.
Also, EDIT:in the wiki page anouncing this beta version at [http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta), there was this text informing how users could upgrade to it from breezy:
> gksudo "update-manager -d" * The "-d" switch instructs Update Manager to consider **pre-release versions**, including this Beta release.
which would mean that by the time a new release is released (ahah), update-manager will detect it (since update-manager is always running in ubuntu. EDIT:actually, update-notifier is always running...).

---

### Post by aysiu on 2006-04-23
[QUOTE=jobezone]
Also, EDIT:in the wiki page anouncing this beta version at [http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta), there was this text informing how users could upgrade to it from breezy:[/QUOTE] [Someone on these forums tried to follow those instructions and it apparently didn't work](http://www.ubuntuforums.org/showthread.php?t=164071). I think that person's new, though, and may not have followed them correctly.

Can someone experienced try it out and see if it works, and then post back here the results?

In the meantime, I **know** these instructions work: [http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by kingmonkey on 2006-04-23
Remember: You dont have to upgrade if you dont want to.

---

### Post by sinkxdie on 2006-04-23
Whoa...I did it, installed, upgraded, had a few problems and fixed it. Exept when the loading screen comes up at boot, its all discolored and in a different size. Other then that no real problems.

---

