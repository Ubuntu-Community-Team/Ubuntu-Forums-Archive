---
title: "Wireless help"
date: 2011-08-28
forum: General Help
---

### Post by LatencyRemix on 2011-08-28
I've been using ubuntu on my old PC for a bit and love it.  So now i went and put it on an old laptop i had that was being used as a paper weight.  When i had windows on it i had nothing but problems getting the wireless to work, no it could be that the wireless module has **** it self im not sure.


I've read a few how to's about it.  when i put in 
lspci | grep Network

i get "03:00:0 Network controller: Broadcom Corporation BCM4311 802.11/b/b (rev 01)

and then iwconfig

lo no wireless connection

eth0 no wireless connection

am i wrong to assume i should get a third showing up for the wireless device?

---

### Post by gandaran on 2011-08-29
connect with wired internet and wait a few minutes to update software packages then enable the broadcom driver in additional drivers, this should get your wireless working but if it doesn't follow this thread on how to install the right broadcom drivers.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

