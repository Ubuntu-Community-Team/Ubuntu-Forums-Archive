---
title: "Connection problems with new router"
date: 2011-01-24
forum: General Help
---

### Post by zorblek on 2011-01-24
I recently bought a new router, a D-link DIR-615, and ever since I installed it I've been having weird connection problems in Ubuntu. There are two Ubuntu machines on this network: one that runs Lucid and one that runs Maverick. Neither is having problems connecting to the network, but they both often have problems loading web pages. The Lucid machine gets frequent "Connection was reset" errors, while the Maverick machine usually doesn't show an error message, but many pages will load endlessly. (This might have something to do with the browser used; the Lucid machine uses Firefox and the Maverick one uses Chrome.) When I connect to the network with Windows XP I don't experience these problems, so I'm pretty sure it has something to do with Ubuntu.

Can anyone shed light on this? I'd really appreciate any help.

---

### Post by dcstar on 2011-01-25
> **zorblek said:**
> I recently bought a new router, a D-link DIR-615, and ever since I installed it I've been having weird connection problems in Ubuntu. There are two Ubuntu machines on this network: one that runs Lucid and one that runs Maverick. Neither is having problems connecting to the network, but they both often have problems loading web pages. The Lucid machine gets frequent "Connection was reset" errors, while the Maverick machine usually doesn't show an error message, but many pages will load endlessly. (This might have something to do with the browser used; the Lucid machine uses Firefox and the Maverick one uses Chrome.) When I connect to the network with Windows XP I don't experience these problems, so I'm pretty sure it has something to do with Ubuntu.

Can anyone shed light on this? I'd really appreciate any help.

Check MTU settings on the router, and check the Ethernet settings on the router and on Ubuntu with the **Ethtool** package.

---

### Post by poodoopealeoaph on 2011-01-25
Another thing you can try is to go to "system>administration>additional drivers" and check to see what wireless driver you have selected. I've noticed that if I have the "broadcom b43 wireless driver" I can only connect to certain routers. Since switching to the "broadcom sta wireless driver" i have been able to connect to anything that comes my way.

---

