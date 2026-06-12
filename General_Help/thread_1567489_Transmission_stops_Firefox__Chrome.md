---
title: "Transmission stops Firefox / Chrome"
date: 2010-09-03
forum: General Help
---

### Post by akxiii on 2010-09-03
When I run Transmission, Firefox and Chrome are unable to load pages (ie google.com).

Transmission doesn't even have to be downloading, and the 'turtle' setting can be on also. It doesn't seem to help.

*And here are the specs:*
[LIST]
[*]Ubuntu 10.04 64bit
[*]Chrome 6.0.472.53
[*]Firefox 3.6.8
[*]Transmission 2.04 (11151)
[/LIST]

Maybe some port needs to be defined or something? I have no idea. It used to work fine, when I first installed 10.04.

If there are any other need-to-knows let me know, I'm not sure what else to include.

---

### Post by akxiii on 2010-09-03
No idea what changed, or if a fix came through but the problem stopped. This has been a problem for the better part of 2 months. 

But hey it is working so I won't complain just because I don't know why.

---

### Post by ias on 2010-10-29
Exactly the same problem here. Why is the 'solved', if there is no solution given?

---

### Post by Demask on 2010-11-02
> **ias said:**
> Exactly the same problem here. Why is the 'solved', if there is no solution given?

Same problem here too, as long as there is a download active (even if it is not seeding/downloading) Firefox/Chromium grinds to a halt. Every webpage I try to load times out, anyone know why this is happening?

[Edit]
Oh, better throw in some specs to:
Ubuntu 10.10
Transmission 2.04
Firefox 3.6.12
Chromium 6.0.472.63

Oh, and it just started working again for no apparent reason. Maybe leaving Transmission up and running for a while somehow helps?

---

### Post by ias on 2010-11-02
I managed to sort this out by turning off 'flood detection' in my cable-modem-cum-router (cisco)
(kinda copy-pasting )

Cisco EPC3825IP Flood detection



* Connect the computer to a modem with the wire or wireless  and go the address
 [http://192.168.0.1](http://192.168.0.1) * log in ( usually leave username and password field empty)


1. Choose "Security"
2. Uncheck  "Block IP Flood Detection"
3. Press "Save Settings"

You could try this also: NAT = Network Address Translation (take it off)



* Connect the computer to a modem with the wire or wireless  and go the address
 [http://192.168.0.1](http://192.168.0.1) * log in ( usually leave username and password field empty) Käyttäjätunnus ja Salasana jätetään tyhjäksi)


Choose   "Administration"

Choose "Working Mode:" ->  "Bridged only"

Press "Save Settings"

---

