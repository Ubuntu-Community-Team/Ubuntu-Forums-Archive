---
title: "Wireless Died"
date: 2006-06-09
forum: General Help
---

### Post by Mau on 2006-06-09
Hello everyone,
On my Kubuntu laptop, the wireless is no longer working.  I did not change any configurations AFAIK.  The light on my wireless card lights up and doing sudo ifup eth1 works fine.  My routher also acknowledges that my computer is connected, but I can't access the LAN or the Internet.

I believe I did an apt-get update last night (not certain), but all it updated was some font libraries.  Any idea what is going on? It used to work perfectly and the reason why I picked Kubuntu was because of the wireless support.

---

### Post by Dr. Nick on 2006-06-09
Im not using kubuntu but in ubuntu if your wired card is enabled then the wireless doesnt work well. Just something you might look into if applicable

---

### Post by Mau on 2006-06-10
I figured out it has something to do with a firewall I must have installed (or via a dependecy).  After each reboot, my solution to getting online is to install guarddog and then uninstall, which disables the firewall.  How do I automatically disable it or set it so I can connect?

---

