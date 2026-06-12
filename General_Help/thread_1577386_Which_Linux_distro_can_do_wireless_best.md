---
title: "Which Linux distro can do wireless best?"
date: 2010-09-18
forum: General Help
---

### Post by rbrauns on 2010-09-18
Hi,

I just built a new HPTC. Abit AN-M2HD, Athlon 64, 4GB, 2TB HDD, DVD ROM, Nvidia onboard graphic chip, wireless Logitech keyboard and wireless mouse, 27" Acer B273 monitor.

The wireless keyboard and mouse work under Ubuntu no problem.  My frustration is the wlan card.  I have 2 PCI wireless cards, both Dlink: one with a BCM4306 chip, the other with a Marvel W8300 chip and a USB WUA-2340 stick from Dlink. No amount of fiddling with Ubuntu seems to get any of these wireless devices working. However, I've made the most progress with Ubuntu which recognizes my BCM4306 and assings wlan0 to it.  I've also tried Mint, OpenSuse and Fedora and not one Linux version works. Most identify the BCM4306 on the PCI bus but then it doesn't connect to the internet. Oddly enough, my wireless keyboard and mouse, both of which have USB dongles, work just fine. So does Windows XP. 

I really want to move away from well, um, cracked software and use Linux. So, here's my question: which Linux distro can do wireless best?

Thanks, Rob

---

### Post by davrosuk on 2010-09-18
No distro is really going to be better than any other when it comes to those. The D-Link one is a Broadcom chip who have only very recently decided to commit to producing linux drivers. The other is pretty old from what I can make out and no linux drivers exist for that either. You might want to have a look at ndiswrapper which allows you to use windows drivers in linux.

---

### Post by TheMixtureMedia on 2010-09-18
Hey I run all Dlink and it works for me out of the box for 10.10 with no issues.

---

