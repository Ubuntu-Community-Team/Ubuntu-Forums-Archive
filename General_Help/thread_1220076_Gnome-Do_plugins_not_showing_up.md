---
title: "Gnome-Do plugins not showing up"
date: 2009-07-22
forum: General Help
---

### Post by fox303 on 2009-07-22
Hello all. I've been searching the www up and down, reading the Gnome-Do Wiki forwards and backwards but I can't seem to figure this one out. 

I've installed the lates Gnome-Do package 0.8.2 from their PPA. Everything went smooth. However, when I browse the list of the official or community plugins, they're both empty. I can't install any plugins whatsoever. 

And there's another element to it. I also installed the latest Cairo-Dock, and even though it's working fine, I can not access the list of themes and stuff that is normally contained within. I already had both, Gnome-Do and Cairo dock working and was able to browse the themes/plugins from the options menu.

I'm running Linux Mint 7 "Gloria" which basically is a modified 9.04 Jaunty. System has been freshly setup, and is up-2-date and pretty much factory-default.

Any help on this issue would be greatly appreciated. Cheers.


Oh and on a second thought .. I already tried running the programs with gksudo because I thought it might be a permissions problem but still the plugins won't show up.

EDIT - Update: I figured out parts of the problem. Even though I am - as you can see lol - connected to the internet. I could receive email and browse the web, but it appears as if some applications think I am offline. I fixed that partitially by deleting the network connections that were present, and by creating a new connection manually ( I use a static IP ). So at least I can access the Gnome-Do plugin list now and it works like a charm. Cairo Dock however still doesn't show any available themes.

---

### Post by fabounet on 2009-07-22
are you under a proxy ?
CD uses *wget* to retrieve the list of themes, so you have to make *wget* work on your PC

---

### Post by marcon00 on 2009-07-24
> **fox303 said:**
> Hello all. I've been searching the www up and down, reading the Gnome-Do Wiki forwards and backwards but I can't seem to figure this one out. 

I've installed the lates Gnome-Do package 0.8.2 from their PPA. Everything went smooth. However, when I browse the list of the official or community plugins, they're both empty. I can't install any plugins whatsoever. 

And there's another element to it. I also installed the latest Cairo-Dock, and even though it's working fine, I can not access the list of themes and stuff that is normally contained within. I already had both, Gnome-Do and Cairo dock working and was able to browse the themes/plugins from the options menu.

I'm running Linux Mint 7 "Gloria" which basically is a modified 9.04 Jaunty. System has been freshly setup, and is up-2-date and pretty much factory-default.

Any help on this issue would be greatly appreciated. Cheers.


Oh and on a second thought .. I already tried running the programs with gksudo because I thought it might be a permissions problem but still the plugins won't show up.

EDIT - Update: I figured out parts of the problem. Even though I am - as you can see lol - connected to the internet. I could receive email and browse the web, but it appears as if some applications think I am offline. I fixed that partitially by deleting the network connections that were present, and by creating a new connection manually ( I use a static IP ). So at least I can access the Gnome-Do plugin list now and it works like a charm. Cairo Dock however still doesn't show any available themes.

i'm having the same problem wit Mint 7 :) i will try solving it the way u did, but i dont have static IP ...


EDIT: you did try installing it from the packet manager ? :p gnome-do-plugins

---

