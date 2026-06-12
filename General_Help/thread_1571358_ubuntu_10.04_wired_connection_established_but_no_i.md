---
title: "ubuntu 10.04 wired connection established but no internet"
date: 2010-09-09
forum: General Help
---

### Post by saixdeejay on 2010-09-09
hi all!!
i have just installed ubuntu 10.04 on my laptop hp 550.after i finished installation i connected to internet via eth0 wired connection normally and everything was fine...after about 1 hour i had no internet....i try restart but is the same problem....this is strange because my eth0 says connection established and when i open mozilla i cant open google either.....when i ping [www.google.com]("http://www.google.com") it says "cant resolve "

my internet works fine in windows so what should i do to have back my internet on ubuntu...i cant do anything else in ubuntu if i have not internet and i like very much ubuntu so

please help me !!!

---

### Post by mkmcllln on 2010-11-04
saixdeejay, I had the exact same problem.  I read a tonne of posts to try and find the resolution.  It seems odd, but it looks like you have to hard reset the NIC.  So, turn off your copmuter, unplug the computer and if wired, ethernet cable, (if you have a laptop, take out the battery) and wait a while.

Then go to your interfaces file

```
sudo gedit /etc/network/interfaces
```

and make sure it only has

```
auto lo
iface lo inet loopback
```

Hope that helps.

---

### Post by ValBlue on 2011-04-04
ok and if appears this in the interface 

what are we do next?

---

### Post by Maverick Mungbean on 2011-06-18
> **ValBlue said:**
> ok and if appears this in the interface 
 
what are we do next?
 what next?

---

