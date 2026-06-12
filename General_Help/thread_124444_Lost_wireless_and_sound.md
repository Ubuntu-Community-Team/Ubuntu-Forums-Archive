---
title: "Lost wireless and sound"
date: 2006-02-01
forum: General Help
---

### Post by ked on 2006-02-01
Running Ubuntu on an Acer TravelMate 4650 laptop with great sucess for 6 months until yesterday!

The sound does not worry me but loosing wireless does...
Tried reinstalling ipw2200 and ieee80211 as described in the forums without success.

Everything with networking during boot take ages and 'touch' complaints '/var/lock/subsys/hotplug' does not excist.

I think some part of the filesystem is corrupted because searching files with 'find' give warnings about inconsistensy in the /proc directory

I hate to ask, but is there any tools in Ubuntu like the 'System Restore' in WinXP ?

Normally if I play around a bit I'm solve most of the problems I run into but in this case I'm completely LOST please HELP!!!

---

### Post by lamego on 2006-02-01
If you believe you have file system inconsistensy you should boot on single user mode or from a live cd and check it with the "fsck" command.  It will repair the problems (if any) .

---

### Post by ked on 2006-02-01
[QUOTE=lamego]If you believe you have file system inconsistensy you should boot on single user mode or from a live cd and check it with the "fsck" command.  It will repair the problems (if any) .[/QUOTE]

I'll definetively give it a try!!!

---

