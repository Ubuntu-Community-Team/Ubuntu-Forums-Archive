---
title: "localhosts problem / question"
date: 2009-07-18
forum: General Help
---

### Post by Twizzle on 2009-07-18
I have Ubuntu 8.10 server edition installed and have been playing around with mpd and jinzora and MPoD to try and set up a link to my HiFi which can be controlled via my laptop and iPhone.

So far things are working but I seem to have a problem with some of the config scripts on the server.

In several places I have seen the script refer to 'localhost' which I assume means the server it is on (I am quite new to Ubuntu) the only problem is I have to change this to 192.168.1.101 to actually get things to work. It is getting a bit of a pain the more things I set up and I assume that this is not good practice and that I have a problem somewhere else.

My /etc/hosts file reads:

127.0.0.1       localhost
127.0.1.1       thegcs
192.168.1.101   thegcs.co.uk    thegcs

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

