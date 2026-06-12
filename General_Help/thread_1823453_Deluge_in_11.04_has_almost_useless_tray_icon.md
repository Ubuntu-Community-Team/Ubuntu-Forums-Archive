---
title: "Deluge in 11.04 has almost useless tray icon"
date: 2011-08-12
forum: General Help
---

### Post by mfearby on 2011-08-12
The other day I upgraded from 10.04 > 10.10 > 11.04 and have found (among other annoyances/regressions) that the Deluge tray icon no longer lets me control the up/down speeds. I do this semi-regularly according to what I'm doing/downloading (and not to hard-and-fast time schedules), and would like the good old-fashioned tray icon/menu back. Does anybody know if there's a way to reinstate the fully functional menu? I couldn't identify a preference option for it.

I downloaded kubuntu 11.04 today and wasn't turned off. I was driven to GNOME when KDE 4.0 came out, and have actually grown to quite like GNOME 2.x and dread the thought of leaving it, but now that even "GNOME Classic" in Natty is beginning to suffer the death of a thousand cuts, I may just switch to kubuntu, but would like to try and stick it out with GNOME for a while.

---

### Post by el_koraco on 2011-08-12
Install dconf-tools
Open dconf-editor with ALT+F2
Go to Unity, panel, systray-whitelist or something like that, and add Deluge to the apps. I think that should make it use a panel applet instead of the indicator.

---

### Post by mfearby on 2011-08-12
Thanks. I tried that to no avail. I added "deluge-gtk" (same as process name, so I assume it's right) to "desktop > unity > panel > systray-whitelist" and logged out and in again. 

BTW, I'm usinge "GNOME Classic" and am not using the new Unity desktop shell. Not sure if that's relevant. I also [did this]("http://halfclosed.wordpress.com/2011/05/05/quick-fix-natty-ubuntu-classic-and-compiz/") to fix compiz after the upgrade.

---

### Post by mfearby on 2011-08-12
I just changed it to ['all'] as per the advice in the program itself, logged out and in again, and the menu from the tray icon is still useless. I suppose the developers must have allowed GNOME's "less is more" and "we know best" philosophy to infiltrate their minds, sadly.

That's one thing I remember about the good old days in KDE 3; it always allowed the user to have full control (sometimes too much control). You rarely heard of a KDE developer deciding to force everybody to do something his/her own way. 

I don't mean to rant but I've gone at least two years without feeling the need to whinge about Linux but 11.04 and its various regressions have given me cause to sit up and take notice again.

Admittedly, it's only a torrent program, so that's hardly GNOME's fault, but Unity/GNOME 3 are *far* worse than Deluge's almost innocent-by-comparison ditching tray menu usability.

KTorrent was overloaded with preferences. I'll check it out in my Live CD tonight and reminisce about the good old days of being in control of my PC again :-)

Thanks for your help.

---

### Post by Cas07 on 2011-08-12
To enable the old systray, which is what is being suggested, you need to uncheck Application Indicator in Preferences.

I should mention that at the time of development, just before Natty release, there was a major bug in App Indicator library that meant we could not create submenus and thus not implement speed changing. We also have limited time to work on every area of Deluge so some parts, such as user interface changes, lag behind.

There was a discussion recently on our forum about App Indicators if you wish to know more:
[http://forum.deluge-torrent.org/viewtopic.php?f=10&t=37229#p156143](http://forum.deluge-torrent.org/viewtopic.php?f=10&t=37229#p156143)

---

### Post by mfearby on 2011-08-12
It would seem that said preference option has been stripped completely from Deluge 1.3.1. But never mind, I have Kubuntu 11.04 setup in a VM and it's quite nice. KDE has finally recovered from their botched 4.0 release, and now that GNOME/Unity see fit to follow in their footsteps and botch their new releases (and then some!), I can see a full format/reinstall coming on this weekend :-)

Thanks anyway for your assistance.

---

### Post by Cas07 on 2011-08-13
If you upgrade to 1.3.3 from our PPA it will have the option:  [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

---

