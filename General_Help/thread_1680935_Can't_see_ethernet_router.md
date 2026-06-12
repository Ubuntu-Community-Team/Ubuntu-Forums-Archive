---
title: "Can't see ethernet router"
date: 2011-02-03
forum: General Help
---

### Post by sbelz79 on 2011-02-03
I connect to a Linksys Wireless-B router in my home.  My connection was working fine last night, but when I booted up my computer this morning, nothing shows up in my list of available connections.  I've tried disconnecting the router from its power source for a minute, I've tried rebooting my computer.  I booted my computer using an Ubuntu 9.10 64-bit live CD, and I was able to connect just fine, so I know it's not an issue with my mobo's onboard ethernet.  But it's still not working when I boot from my hard drive.  I'm running 10.04 64-bit.  I've had this problem once before in the year-plus since I built this machine, but it resolved itself after I rebooted a couple of times.

---

### Post by psusi on 2011-02-03
Your ethernet controller is on the fritz.  Check /var/log/messages for errors, and try completely removing power from the machine rather than just rebooting.

---

### Post by sbelz79 on 2011-02-03
> **psusi said:**
> Your ethernet controller is on the fritz.  Check /var/log/messages for errors, and try completely removing power from the machine rather than just rebooting.

Shutting off the PSU for a minute and then turning it back on before booting fixed the problem, so I'll consider the problem resolved.  I'm not an advanced enough user to know what I'm looking for in /var/log/messages, but if there's something specific you would like to see, by all means let me know.

---

