---
title: "Network Detection"
date: 2006-05-23
forum: General Help
---

### Post by Irony on 2006-05-23
Quite often I boot up and the network isn't detected which means I can't get onto the net - the result is I have to reboot.

Is there some command I can use to simulate the network detection phase without rebooting?

---

### Post by W. Irving on 2006-05-23
```
sudo ifup eth0
```
Should do it.
Or ath0 if you're on a wireless network.

---

### Post by Irony on 2006-05-23
Hey thanks, I did a google with that command so I now know what I'm doing!

---

