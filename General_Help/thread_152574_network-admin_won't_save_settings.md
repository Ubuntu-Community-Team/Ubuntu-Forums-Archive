---
title: "network-admin won't save settings"
date: 2006-03-30
forum: General Help
---

### Post by youngerpants on 2006-03-30
Hi,

I have my breezy box set up to pick up its IP address via DHCP. However, I have had to change this to a fixed IP so I can setup openvpn. if I use network-admin to do this, I can save the basic IP settings for the ethernet controller (eth0), however, it wont save any DNS settings. 

I add my router as the DNS server (192.168.0.1) and click OK, but when I try to ping externally, I dont get a reply. If I re-open network-admin and click on the DNS tab, my settings revert back to 127.0.0.1

Can anybody guess why this is happenning and knows of a way to resolve the issue.

Many thanks

Younger

---

### Post by Zimmer on 2006-03-30
[http://ubuntuforums.org/showthread.php?t=151096](http://ubuntuforums.org/showthread.php?t=151096)
See post #10
This guy was having trouble with the network card settings reverting at bootup.
Perhaps your answer lies with the ROM (I think he meant BIOS) settings for your machine.

---

