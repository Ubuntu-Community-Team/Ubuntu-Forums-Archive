---
title: "Packet Tracer"
date: 2010-03-09
forum: General Help
---

### Post by gareth547 on 2010-03-09
Im new to Ubuntu and have just installed the packet tracer from cisco via wine and every time I open the file it flash's up a message  that reads the package as shut down

---

### Post by fstab on 2010-04-16
I can't help too much with your Wine / Cisco app situation but I can tell you about some IP tools available in Linux that you can try if you don't have to use the Cisco/Wine app. 

The command 'traceroute' from inside a terminal will trace a route to a destination, showing all the router hops along the way.
Eg: 
traceroute [www.google.com](www.google.com)

If you're looking for an IP capture solution that displays all the IP traffic on your network interface, you can try the applicaiton WireShark.  Here's how to install and launch it from a terminal...

# this installs wireshark
sudo apt-get install wireshark wireshark-gnome

# this starts wireshark
sudo wireshark

---

