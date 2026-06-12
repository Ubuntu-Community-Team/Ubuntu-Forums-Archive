---
title: "Network Manager"
date: 2011-05-14
forum: General Help
---

### Post by steveodeevo on 2011-05-14
Since upgrading to 11.04 Natty, I seem to have a strange bug with my network connection, essentially I am connected to my network with the same settings and IP address I entered during the installation, which I can see when I type *ifconfig* into a shell, and in my */etc/network/interfaces* configuration as auto eth0, however the network manager shows no connections, and if I click on the *connection information* option it tells me there are no active connections, when there plainly is.

As best I can figure it is like the system is configured as if via the command line and for some reason the network manager in natty isn't able to read this configuration.

I am not very clued up when it comes to why this wouldn't work, is there any chance someone out there might have a solution?

I did a quick google and also a search on the forums here, however as you can imagine when asking about network connection problems you get a lot of responses for the network not connecting and not for being connected but with no icon.

---

### Post by ManualSparrow on 2011-05-14
Well, you could reinstall the Network Manager in Synaptic and see if that fixes it. You could also run ```
sudo dhclient wlan0
``` to reconfigure your DHCP stuff, but I am not sure if that is the right fix.

---

### Post by steveodeevo on 2011-05-17
The solution I used in the end was to go to /etc/network/ and mv interfaces to interfaces.old, and then touch interfaces and chmod it to 0777 and reboot, after that the network manager detected the networks again, they all appear in the list.

---

