---
title: "problem connecting wireless using LEAP"
date: 2010-05-10
forum: General Help
---

### Post by the_last_don on 2010-05-10
Hi
I'm using ubuntu for about 3 years, and I update my machine each 6 months with the latest version.

In the past, in order to be able to connect to IBM wireless network (LEAP) I had to enabled a restricted driver in the "System>Admin>Hardware Drivers" restricted drivers manager.

I think it was Intrepid, or (Hardy), that since then the restricted driver to the wireless card is not appear in the restricted drivers manager.

I'm using Thinkpad T60, Ubuntu 10.04, the Ethernet controller is Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
(attached the output of lspci command)

BTW - I have no problems connecting to regular wifi networks.

Hints anyone ?

-- The Last Don

---

### Post by the_last_don on 2010-05-10
Attached is the output of /var/log/syslog during the attempts to connect and the screen-shot of the network configuration 

I hope it will put some lights on my problem 

-- The last don

---

### Post by the_last_don on 2010-05-10
Here are the attachments :-)

---

### Post by deezer on 2010-05-20
Don,
I am having a similar problem - on a Thinkpad T500 on a CISCO wireless network.  Were you able to determine anything?

---

### Post by deezer on 2010-05-21
I was able to get my problem fixed - as it turned out "WPA Enterprise", choosing LEAP as the authentication method was just what I needed....

---

### Post by abdusamed on 2010-06-03
I can't connect to a WPA2 secured network on ubuntu 10.04. Only non-secured which isn't good for an ad hoc network! plz... my dual boot wins 7 has a virus.. can't open browser or anything!

---

### Post by deezer on 2010-10-25
> **abdusamed said:**
> I can't connect to a WPA2 secured network on ubuntu 10.04. Only non-secured which isn't good for an ad hoc network! plz... my dual boot wins 7 has a virus.. can't open browser or anything!

What type of WPA2 network?

---

### Post by abdusamed on 2010-10-25
secured obviously... It for some reason only is able to connect to non secure ad hoc networks.. i pretty much gave up and I'm not interested in any solution

---

