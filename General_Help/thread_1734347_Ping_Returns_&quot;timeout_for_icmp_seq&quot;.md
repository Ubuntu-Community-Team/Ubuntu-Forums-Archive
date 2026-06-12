---
title: "Ping Returns &quot;timeout for icmp_seq&quot;"
date: 2011-04-20
forum: General Help
---

### Post by josephmcnelis on 2011-04-20
Hi All,

I recently got a new VPS but when i tried to ssh in i couldn't, so i pinged the IP and got

"Request timeout for icmp_seq"

After contacting technical staff they said there was a problem on startup, and i was to use the console provided and "fsck", i messed around with this for a while then contacted technical help again and they replied.

"It's pinging now. Error in your interfaces file, I've manually configured the eth0 for you but make sure to edit /etc/network/interfaces."

And indeed it was pinging, so i rebooted the machine and then it went back to the way it was. So im assumingin doing so i have reset the file back to the broken version and thus i have to edit the interfaces file to make it work again, this is new to me so can anyone offer any suggestions.

My current interfaces file:

auto etho0
iface eth0 inet static
address xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx
netmask 255.255.255.128
auto lo
iface lo inet loopback

---

