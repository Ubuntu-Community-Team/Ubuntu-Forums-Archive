---
title: "finding out the routers's ip"
date: 2011-08-13
forum: General Help
---

### Post by loolooyyyy on 2011-08-13
it's been asked million million times
and billion billion answers have been given
BUT none of them worked for me
the ip is 192.168.0.1
but what if i changed it somehow and forgot it? how do i find it?
ifconfig gives my own ip: 192.168.0.2
netstat -nr gives a bunch of addresses including 192.168.0.0
but nowhere i can see the 192.168.0.1?

---

### Post by haqking on 2011-08-13
this is a continuation of your original thread at [http://ubuntuforums.org/showthread.php?t=1824195](http://ubuntuforums.org/showthread.php?t=1824195)

bad form to post multiple threads ;-)

netstat -r will list the gateway address.  anytthing with all 0 is the network and 255 is broadcast

---

### Post by cwwilson721 on 2011-08-13
9 times out of 10, if you are using DHCP to get addresses (and if it is the only router on your network, assuming it's a home network, too), the router's IP is the Gateway IP address of the device used to connect to the router.

Ex: Home network, PC w/Ubuntu using DHCP to get addresses, cable modem.

PC requests IP address, Router gives internal LAN address to PC, along with Gateway IP, DNS Server IP, and a few other things.

Looking in Network Manager > Connection Information, look at "Default Route". Odds are, that's the Router IP address. (Also assuming IPv4)

---

### Post by loolooyyyy on 2011-08-13
no i wasnt making multiple threads!
i had 5 questions that i just asked them together today!
i hate making multiple threads, sorry if it looked like this

---

### Post by loolooyyyy on 2011-08-13
cwwilson721 is right, tanx
now i can fix my uncle's network

---

### Post by haqking on 2011-08-13
> **loolooyyyy said:**
> no i wasnt making multiple threads!
i had 5 questions that i just asked them together today!
i hate making multiple threads, sorry if it looked like this


looks like same discussion im already having with you in the other thread.

---

### Post by loolooyyyy on 2011-08-13
hmmm, maybe, but i didnt mean to do this
soooo, now that we all know i didnt mean any harm to ubuntuforum and i love it and have great respect, could you please answer to the other forum's question? tanx again

---

