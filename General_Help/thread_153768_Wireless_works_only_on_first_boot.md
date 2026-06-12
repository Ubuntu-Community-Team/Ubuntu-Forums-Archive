---
title: "Wireless works only on first boot"
date: 2006-04-01
forum: General Help
---

### Post by ubuntukid on 2006-04-01
I configured my Belkin wireless card during installation and it worked strait away. All I had to do was tell it my network name, etc. But once the computer has been turned off it is no longer able to connect. In fact it can't even see the network. I thought I needed to install a driver but the weird thing is that EVERY time I install either ubuntu or kubuntu it is always capable of using my card and connecting to the internett, but as soon as I do a reboot, that's it. No more networking for me.

Is this some sort of bug or am I doing something wrong?

I'm using 5.10.

---

### Post by ren wins on 2006-04-01
i know 3 commands for networking, wireless or otherwise
and magically, some combination of them can get my wireless up and running

they are ifup, ifdown, and dhclient

you should also check out ndiswrapper to get your wireless card's drivers to work

---

### Post by ubuntukid on 2006-04-01
I did think about using ndiswrapper but I wouldn't think it would be needed as it worked the first time I booted the computer without any problems. But I'll try the programs you mentioned.

---

### Post by jamesr on 2006-04-01
Lets see if the NIC is seen```
sudo ifconfig -a
sudo iwconfig -a
```

---

