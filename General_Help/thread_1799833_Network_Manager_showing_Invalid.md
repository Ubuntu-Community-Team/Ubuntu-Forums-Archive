---
title: "Network Manager showing Invalid"
date: 2011-07-08
forum: General Help
---

### Post by Dobbie03 on 2011-07-08
I have just intsalled Gnome3 and GS with the Ricotz ppa.  My network manager is showing as invalid, I am still connected to the net but I cant do anything with my network settings.

how do I fix this?

Here is a screenshot:
[http://i.imgur.com/yUJJh.jpg](http://i.imgur.com/yUJJh.jpg)

---

### Post by teddybairs1 on 2011-07-14
Hey, mine did the same thing. I shut off my laptop and when I went back to it the next day thinking I was going to have to do some major package gymnastics and found that the network manager was working under Gnome 3, but was still showing invalid under KDE even though the network was working.

When I launched gnome-nettool from the file manager in /usr/bin it showed everything working fine. I think somehow the gnome 3 packages are superceding everything from boot. I noticed that efter that update nautilus runs at startup even in KDE. I tried disabling it and it still runs at startup, so there's something somewhere in the system from GNOME 3 which is launching on it's own irregardless of the DE in use. If you're using Gnome 3 as your DE then it shouldn't be an issue, but it's darned annoying when using KDE on the same system.

---

