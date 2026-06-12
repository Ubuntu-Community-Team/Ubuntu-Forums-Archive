---
title: "network help - avahi not brodcasting properly."
date: 2010-07-11
forum: General Help
---

### Post by darthpenguin on 2010-07-11
I don't know if this is a Mac issue, router issue, Ubuntu issue, or a combination thereof, but I thought I'd start a post here because the forum is always so darn helpful. Basically I'm trying to set up file sharing between Mac and Ubuntu. It works mostly, but it's buggy. All my macs are connected to the network (some witlessly) and sharing files using afp. If a Mac is turned off or disconnected from the network in any way (ie. laptop is closed) or the file sharing is disabled this is IMMEDIATELY apparent to all other Macs. The server disappears from Finder's sidebar right away. The revers is also true. As soon as a Mac connects to a network it is found by all other Macs on that network.

Ubuntu isn't doing this. I have followed tutorials and setup Avahi with netatalk. shares on Ubuntu show up in Mac Finder ONLY if I restart the avahi-daemon on Ubuntu. If I take my Macbook out of the network and bring it back it will not find Ubuntu until I restart the avahi-daemon on the server. Also, if I turn off the Ubuntu machine (or disable it's network connection or unplug the Ethernet) the entry in Mac's Finder for ubuntu will still be there (Mac doesn't know the server is inaccessible) so all I have is a useless entry in Finder's sidebar. I don't think it's a netatalk issue because the same thing happens if I use samba. I also have a similar problem with my PS3 picking up my mediatomb server (it won't unless i restart mediatomb).

This sucks. how can i get my devices to find my services running on ubuntu automatically? I hate restarting services all the time.

---

