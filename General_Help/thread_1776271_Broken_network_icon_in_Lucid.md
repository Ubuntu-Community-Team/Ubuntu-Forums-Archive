---
title: "Broken network icon in Lucid"
date: 2011-06-05
forum: General Help
---

### Post by Ernesto RD on 2011-06-05
I use 10.04 Lucid on my Dell mini10v netbook, it works fine, but the network status icon is broken.
When i connect to my wired network, the icon correctly changes to the 2 "arrows" that show that the wired connection is active. But when i dissconnect the wired network, and i connect to my wireless one (or any wireless network), the icon has the "X" (not connected) mark, even thoug the network IS properly connected (i can access internet, local network, etc).

I know this is not a "critical" bug, but its annoying. Anyone else has this problem? and, is there a way to fix it?

Thanks

---

### Post by pqwoerituytrueiwoq on 2011-06-05
what theme are you using?

---

### Post by Ernesto RD on 2011-06-05
> **pqwoerituytrueiwoq said:**
> what theme are you using?
Right now the "default" one. But i tried with several, and it seems the problem is un-related to the theme, because it happens with all of them.

---

### Post by pqwoerituytrueiwoq on 2011-06-05
here is a copy if the icons on my system (ubuntu 10.04.2)
extract to /usr/share/icons
it should then fix itself sooner or later (when the cache expires)

---

### Post by Ernesto RD on 2011-06-06
Thanks!
unfortunately it dint get a chance to test it, suddenly my netbook doesnt boot anymore. I did NOTHING to it (dint alter configuration, dint install anything new).

You know, on a side note, this has allways bothered me about ununtu, instead of the perpetual "race" to deliver a new version every six months, with new "features" like unity, i think most ppl (myself included), would prefeer if the developers spent more time fixing BUGS in the current releases, and hence providing a more STABLE os.
What i mean is, i would prefeer to see a new STABLE version of ununtu every 2 years, than a buggy version every 6 months.

Im currently downloading opensuse 11.4 to replace lucid on this box, and im allready evaluating fedora 15.

Maybe sometime in the future, ubuntu will change its "upgrade, release cycle, BUG FIX" policies (and hopefully get rid of unity hehe) and ill come back to it.

Thank you and everyone else who has helped me in this forums during my ubuntu experience.

---

### Post by Ernesto RD on 2011-06-09
Ok, my little "damn ubuntu" rant is over :p
I found out why my netbook dint boot (my fault not ubuntu´s). Sorry, i guess i got frustrated.

pqwoerituytrueiwoq: i installed your icons, but the problem persists, i tried changing icon themes to several others, but its the same thing.

i login, the network icon changes to its "connecting" state, then i get the notification that my wireless connection is now connected. And in fact, i can browse the net, access my lan, etc, if i hover my mouse over the icon it even sais "Network connection <<Auto MIDNIGHT>> is active.
But the icon itself is the Disconnected icon! instead of the connected one! :(

Im fresh out of ideas.

Any aditional help would be much appreciated.

---

### Post by Ernesto RD on 2011-06-10
I just cant figure out.
ibe googled, edited the nm-system-settings.conf file, uninstalled and reinstalled network manager, messed arround with the theme icons, and nothing. Network is connected, but icon sais disconnected.
This wouldnt bother me so much, but i need that icon to work properly because it tells me the signal streinght.

checkout the attached image, the network **IS** connected! but icon sais otherwise.

I dont think its a theme problem, i think it goes deeper into the network configuration.

btw, shoudnt wireless devices be "wlan0, wlan1, etc..."?
my configuration sais that my wired network is eth0 and my wireless **eth1** (not wlan0).
Is this normal in ubuntu? maybe the icon problem is related to this?

---

### Post by Ernesto RD on 2011-06-19
oh never mind.
Ibe moved on to other distros that focus more on testing, quality control, and providing upgrades and bug fixes to their current distros in order to deliver a *****STABLE***** operating system, than spend all their time designing an endless stream of new "engeneering wonders" like "me" menus, the "invaluable" little envelope called "messages indicator", and unity desktops.
I guess ill have to learn to live without me menu, unity and all those "wonders".
I wonder if 11.10 will have Funny dancing little pupets on the desktop.

I aplogolize for this rant, but ibe allways loved ubuntu, and i cant help feeling anygry and impotent watching my favorite distro getting more UN-stable, and buggy in every new version, because the people who make it decided to focus all their efforts to implementing new "features" at the expense of working out bugs, testing and providing upgrades to provide a STABLE platform.

---

