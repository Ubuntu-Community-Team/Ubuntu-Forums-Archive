---
title: "Lucid 10.04 Netbook Edition: Battery time halved..."
date: 2010-05-09
forum: General Help
---

### Post by biltong on 2010-05-09
I installed Lucid 10.04 Netbook edition on my Samsung NC140 and was shocked to find out that my battery time has halved from 10 hours to 5 hours.  Before I had Koala Netbook remix (out of the box, no customisation)  installed with great battery life.

Apparently this has to do with the Laptop_Mode:

**cat /proc/sys/vm/laptop_mode** gives me **0 ** (which I guess means not enabled)

**sudo echo 5 > /proc/sys/vm/laptop_mode** works until I reboot. 
**echo 5 | sudo tee /proc/sys/vm/laptop_mode** does not change anything.
Manual edit of file also does not work.

I also found that I do not have /etc/laptop-mode/laptop-mode.conf does this mean that the Lucid Netbook edition does not have Laptop_mode installed??  What else could I try before I go back to Koala. :(

The answer lies under this rock....[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1466241&page=3](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1466241&page=3)

---

