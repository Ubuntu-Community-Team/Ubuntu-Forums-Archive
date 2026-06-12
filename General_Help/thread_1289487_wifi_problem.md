---
title: "wifi problem"
date: 2009-10-12
forum: General Help
---

### Post by _maat on 2009-10-12
Hello,

fisrt of all i'm sorry to post such a message as there are already thousands of them... but i can't find the answer to my problem...

i was using ubuntu for a while now without any wifi problem but switched to ubuntu server a few days ago, and here come the troubles. from what i gathered my wireless card is well detected (correct name appear in a lspci) and can scan networks as well. but my network never appears. i can see 10+ of them but not mine...

for information purposes the network is not hidden and fully available on other computer (windows, mac and linux). so i'm not really sure where the problem may come from.... any thoughts?

edit: 

lspci -k tells me that i use "rt61pci" module
lshw -C confirms that my card is correctly enabled & recognised

---

### Post by Giblet5 on 2009-10-12
You *might* want to replace network-manager with [WiCD]("http://wicd.sourceforge.net/").

I did.

Install WiCD, then uninstall nm via ```
sudo apt-get remove network-manager --purge
``` then set up your networks and as you see fit.

---

### Post by _maat on 2009-10-12
the thing is that i am

1) command line
2) without internet to apt-get anything :p

edit:

from lshw i see that the logical name of my card is wmaster0 and when i "dhclient wlan0" i see : wmaster0: unknown hardware address type 801

---

