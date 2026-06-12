---
title: "Broken Package/Print Driver Issue"
date: 2012-01-06
forum: General Help
---

### Post by Laysan_A on 2012-01-06
Hi,

I was trying to install the latest canon mp610 printer drivers on my wife's laptop (32bit) with Lucid and kde on it. I ran into a dependency issue. I downloaded the debs and put them into /usr/local/src, and attempted to install them, first with gdebi, then with dpkg.

At first, dpkg/gdebi refused to install because libcupsys2 could not be fulfilled. I tried to install libcupsys2 with apt-get, but it said libcupsys2 had been replaced by libcups2, and libcups2 was the latest version.

Assuming that libcups2 was mostly a match for libcupsys, I went ahead and installed both packages (the common and the specific one for my printer model) using force-depends. They installed fine, and though the gui didn't work, the printer was nevertheless recognized by the system, printed, and even had the print head cleaning function in the System Settings - so I'm basically happy - but to the package system, both packages are broken.

The problem is that package management won't let me do any package management without first removing the "broken" packages. I've tried everything I can find to make the system accept them as they are, but I've been completely unsuccessful. I tried a "hold" in dpkg, tried the same in dselect, and tried to find some way to change the flags in apt, but couldn't. I removed and reinstalled about a million times, and I did try some different options, without success, but I can't recall what they were now...

Can someone help me with this?

---

### Post by conradin on 2012-01-06
Im thinking try the generic drivers and see where that gets you. just for a start. But also that dpkg has both an ignore-dependencies and a force option. 
[http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html)

---

### Post by Laysan_A on 2012-01-06
Hi conradin,

Thanks for replying.

What generic drivers? Am I wrong in assuming the generic drivers are already normally present and available to the system when a new device is plugged in? The system was unable to configure anything for this printer on it's own - there were no installed/connected printers at all in the printer dialogue of System Settings. Device manager would dutifully load the printer applet, and send a message that a "new printer is being configured", but ...nothing.

Yeah, I did try --ignore-depends=package, though it's possible my syntax was messed-up. I recall doing it at first without the "=package" part, and it didn't appear to have been accepted, so I remember trying it with the package name, but it's possible (this was a while - and a confusing blur of activity and frustration- ago now) I put it in the wrong place. I may've done it like this: dpkg -i --ignore-depends=packagename.deb packagename.deb, when it should've been like this: dpkg --ignore-depends=packagename.deb -i packagename.deb

I can't get to it right now (she's using it, lol), so it'll have to wait, but I will give it a shot.

---

### Post by Laysan_A on 2012-01-06
I've got good news and bad news...

The bad news first: 

I tried the ignore-depends option and it installed, complained that it wouldn't configure, and STILL got flagged as broken. It didn't work.

Now for the good news: 

It doesn't seem to matter....lol.

I found the system's drivers that you mentioned (they appeared in the appropriate System Settings module), and there appears to be one for the mp610 in there. 

You know, I was a bit confused when I plugged the printer into her laptop and it didn't recognize it. I didn't remember installing drivers for the printer on my desktop, but I do forget these kinds of things on occasion, and decided it was just a lapse of memory...

I guess her laptop was a bit glitchy, and the drivers just weren't showing up until after I tried to install one myself - but they're certainly there now, and the appropriate one seems to work - even with the "new" driver uninstalled. Soooo, I guess I'm good to go! Thanks so much for the help!

---

### Post by conradin on 2012-01-07
Hey, Im glad to hear you're up and running!

---

### Post by Laysan_A on 2012-01-08
Thanks man! :D

---

