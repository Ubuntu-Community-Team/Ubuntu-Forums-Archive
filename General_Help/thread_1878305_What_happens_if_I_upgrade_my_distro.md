---
title: "What happens if I upgrade my distro?"
date: 2011-11-09
forum: General Help
---

### Post by SamusAran on 2011-11-09
Ok So I have Ubuntu 10.04 server installed! Hooray me! this is on a desktop box, with 3 ethernet nic's and a wifi card. any guesses what I use this box for? you got it, my internet domain node. I have xfce installed for my desktop. which makes sense right? 
So the purpose of this machine is as follows: I have DHCP3 server installed, I have BIND9 installed, I have OpenSSH installed, I have Shorewall Firewall installed, I have Hostapd installed, I have compat-wireless installed, I have the ath9k driver, I have disabled/removed network manager, I have samba installed, and finally, I have nvidia video card and alsa sound card. This machine uses shorewall and ipv4 packet forwarding to forward packets for my local domain to the internet. shorewall blocks incoming packets from the net. I use hostapd to set my tp-link wireless card into master mode to act as a wireless access point. i have bind9 running so this machine acts as a caching name server. and I have dhcp to hand out ip adresses on 3 different subnets, 1 for a dmz, 1 for my windows network, and 1 for my wireless clients. and of course i can configure samba and use this machine as a file server.
well anyhow, in the repositories for my distro 10.04 the version of hostapd for this distro is 0.6.9 which is known to have bugs. According to launchpad, if I want to install a never version of hostapd i need to use a higher distro. I want to upgrade to a newer distro so I can install a newer version of hostapd, but as you can tell ive went through a lot of trouble to configure everything. Shorewall was in particular quite a bit of work, and I dont want to lose all of my configuration settings. if I upgrade to a new distro, will all of my configuration files be preserved or overwritten? The majority of these configuration files are in /etc. for example /etc/shorewall/shorewall.conf or /etc/hostapd/hostapd.conf. I'm thinking of upgrading through the gui update manager in xfce, not a live cd, but I want to make sure its safe to do this first. Any thoughts would be greatly appreciated!
 
Cheers.

---

### Post by BenB1 on 2011-11-21
Not completely sure of what would happen but can offer some common sense advise, perhaps.


[LIST=1]
[*]Back up all your configuration data, possibly store it off site and access over a network.
[*]Use aptitude safe upgrade when you upgrade the system. This hopefully will allow leverage to establish your system from a network pull, your back ups.
[*]See number one again, it's important.
[/LIST]


Of course, this merely humble and mad Linux user advice. Your Mileage May Vary, Standard Disclaimers Apply, Take What You Want, Leave What You Don't.


You may also want to check out the Funny Man Pages package and remember if anything is ever taken seriously to an extreme, it becomes ridiculously hilarious by default.

---

