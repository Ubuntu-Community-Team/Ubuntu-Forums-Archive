---
title: "Network speed issues"
date: 2011-03-05
forum: General Help
---

### Post by groonrix on 2011-03-05
I recently installed Ubuntu 10.10 on my machine.
Before, I had Lucid for ~6 months.
When I first installed Lucid, I suffered major network speed issues: basic HTTP pages would not load, I get pongs for only 7% of the pings I send to devices nearby etc.
I tried many offered solutions, till I have been told about *ethtool*.
I changed my connection speed to 10MBs, and speed got better.
 
I saw now that ethtool is now deprecated.
I tried using mii-tool instead:
```
sudo mii-tool -F 10baseT-FD
```
better, but still extremely slow.
Any suggestions?
 
Thanks in advance!

---

