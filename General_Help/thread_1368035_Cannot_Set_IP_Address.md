---
title: "Cannot Set IP Address"
date: 2009-12-30
forum: General Help
---

### Post by isi.catch on 2009-12-30
Hello,

i've been having some issues with setting my static IP address.

this is what i've done so far:



i've edited the /etc/network/interfaces file to look like this:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.80
netmask 255.255.255.0
gateway 192.168.0.1 

```and the /etc/resolv.conf file to look like this:

```

search com
nameserver 196.25.255.3
nameserver 196.25.255.34

```i then reset the the network using this command:

sudo /etc/init.d/neworking restart

i then get the following response

RTNETLINK answers: no such process
SIOCDELRT:no such process

please make provision for my newbie-ness in your replys

thanks

---

### Post by jovean on 2009-12-30
Hi.  I gave myself a static IP in a much simpler (and painless manner): I just replaced Network Manager with Wicd (be sure to reinstall network-manager and network-manager-gnome first in order to have a copy you can reinstall without network access should something go awry).  Then start Wicd from the Networking menu ... and configure your connection there.  It is quite intuitive ... and much easier than I expected.

Hope that helps.

---

### Post by LuisGMarine on 2009-12-30
Well actually I found WICD to be pretty nice, but I like to keep a basic install and not mess around too much.  

Follow this video here on how to set static IP for either you LAN or wireless connection using gnomes network manager.  Very simple to do, and it works like a charm.  

[http://www.youtube.com/watch?v=ClMeY7xKEAU&feature=related]("http://www.youtube.com/watch?v=ClMeY7xKEAU&feature=related")

---

