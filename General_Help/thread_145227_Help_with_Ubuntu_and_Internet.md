---
title: "Help with Ubuntu and Internet"
date: 2006-03-15
forum: General Help
---

### Post by comppsyco on 2006-03-15
Hi Everyone,
I'm a linux newbie, doing my best to migrate from Windows, but I've hit a major roadblock. I have a fresh, clean install of Breezy, and I can't get a network connection to work. I have a Netgear WGR614v6 router that works with all my other machines, as well as the one Ubuntu is on when booted to Windows, and my NIC is integrated with my ECS 848P-A motherboard. First I couldn't get DHCP  to get an IP address, so I gave it a static IP, using the network configuration tool. Then, when I opened Firefox and went to google, instead of telling me right away that it couldn't find a server, it sat and thought and said "Looking up Google.com" for a couple of minutes, then told me that it couldn't find a server. I tried pinging the router, and it told me "Destination Host Unreachable." Please help!

---

### Post by powder on 2006-03-15
Re-enable DHCP, open a terminal and run this command:

sudo dhclient

Post output here if that doesn't work.

---

### Post by comppsyco on 2006-03-15
How's this for weird. After posting my earlier question, I shut down my computer to go eat dinner. Then I came back and booted into Ubuntu, and suddenly I have internet access. I didn't change anything. This has happened to me before, where, without my changing anything, access comes on, and then maybe a couple days later, it's gone again. Any ideas? (I'll go ahead and re-implement DHCP, too)

---

### Post by comppsyco on 2006-03-15
I just re-implemented DHCP, and now I can get an IP. Odd.

---

