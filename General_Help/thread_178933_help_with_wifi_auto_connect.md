---
title: "help with wifi auto connect"
date: 2006-05-18
forum: General Help
---

### Post by Goonie on 2006-05-18
Hi all

I was wondering if someone can tell me what is the best solution to use in order to get my ubuntu to automatically connect to one of my preferred wireless networks on boot? I connect to many different networks depending on where I am at the time and I always have to configure the connection each time I boot in a different location . I tried installing Wifi Radar but that doesn't seem to respond to anything ( I choose a connection and click edit and nothing happens). 

Is anyone doing this successfully?

Will Dapper be an improvement on wireless auto detection and auto connecting?

Thx
Goonie

---

### Post by dsyn on 2006-10-23
I'm in the same boat. figure it out yet?

---

### Post by sleestak240 on 2006-10-23
This is how I set mine up to connect on boot.

Open Terminal
gksu gedit /etc/network/interfaces

Add/edit the section for the adapter you wish to automatically use for connecting.  In my case it's ath0...so something like this:

auto ath0
iface ath0 inet dhcp
wireless-essid the_network_essid_you_want_to_autoconnect
wireless-key xxxxxxxxxxxxx

This is for a DHCP network.  There are some other options you may want/need to set...google or search here for /etc/network/interfaces and you might find them.  If not take a look at the man pages for iwconfig.

---

### Post by dsyn on 2006-10-25
Thanks for putting us on the path :) sleestak

---

