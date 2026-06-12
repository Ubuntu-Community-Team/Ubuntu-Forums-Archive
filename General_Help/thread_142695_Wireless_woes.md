---
title: "Wireless woes"
date: 2006-03-11
forum: General Help
---

### Post by matrisking on 2006-03-11
Hi all,

I'm trying to get my 802.11 wireless card to work at home.  I'm a college student and it works fine connecting to campus networks, but at home it will not connect to the wireless network despite "seeing" that there is a signal, a network, etc.  iwconfig will yield an ESSID, etc.  And it occassionaly tries to send a packet but receives nothing (Somewhere along the line I was messing w/something DCHP related and it would keep attempting to send a packet, get nothing, and eventually yield an error that reads "No working leases in persistent database." 

Any suggestions?  Maybe I need a WEP key?  If so, would it tell me that I need one or just not connect?  Maybe the network does not support the DHCP protocol? Thanks!

---

### Post by andlinux21 on 2006-03-11
Since you are at home who ever set up the router would tell you if you needed a WEP key or not make sure you go into the Networking panel and make sure the card is configured right and that it is activated...

---

### Post by matrisking on 2006-03-11
Yeah, I know it is set up properly, activated, etc.  It works fine on the wireless networks on my college campus.  If I need a WEP key, will the ubuntu networking utility tell me I need it?  Or if I lack a WEP key will it possibly just behave the way I described w/o telling me I need a key?

Sorry, I'm having a tough time describing this easily.

---

### Post by lordofkhemenu on 2006-03-11
[quote=matrisking]Yeah, I know it is set up properly, activated, etc.  It works fine on the wireless networks on my college campus.  If I need a WEP key, will the ubuntu networking utility tell me I need it?  Or if I lack a WEP key will it possibly just behave the way I described w/o telling me I need a key?

Sorry, I'm having a tough time describing this easily.[/quote]
It does seem to me like the router requires a wep key.
Finding the router, seeming to 'connect' but no activity, etc.
I had a similar problem. 
I got tired of dealing with the wep key, set up my router w/ an access list (based on MAC addresses) and problem went away.
Doesnt solve your problem though.

What you could do is - get the admin user and password from whoever set up the router, connect w/ a cable, log in to the router and get the key.
Depending on the manufacturer, the router address might be something like 192.168.0.1 (as it is in my case) , 10.0.x.x... etc

---

