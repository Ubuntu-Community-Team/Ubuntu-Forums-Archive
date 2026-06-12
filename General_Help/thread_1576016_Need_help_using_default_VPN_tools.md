---
title: "Need help using default VPN tools"
date: 2010-09-16
forum: General Help
---

### Post by Magma828 on 2010-09-16
I'm trying to connect to my universities VPN, but I keep getting the error "VPN Connection Failed", which isn't very helpful. The university gives these instructions:

> 
* Start the VPN Client
* Choose New from the Connection Entries menu
* Enter descriptive text in the Connection Entry and Description boxes (eg "University of St Andrews"
* The Host is: 138.251.*.*
* In the Authentication tab choose Group Authentication
* The name is remote and the password **************
* In the Transport tab choose Enable Transparent Tunneling with IPSec over UDP (Nat/PAT).
* Turn off the local LAN Access option, and leave the default timeout value (90 seconds)
* If you are using always-on broadband, in the Dialup tab turn off the Connect to Internet via dialup option.
* If you are using dialup, you need to specify the Phonebook entry that you will be using for the VPN connection
* Click Save

These instructions assume I'm using the Cisco VPN client on Windows, but surely vpnc on Ubuntu is very similar? (if not the same) I'm on 10.04 lucid, btw.

Anyway, if there isn't something I can use to debug the problem, could someone suggest what settings I enter into the form?

---

### Post by Baked- on 2010-09-16
There is a network manager addon that will manage vpnc connections for you.

I like to use the command line version and script it though as i have experienced issues with network manager.  here is some reference for you

[http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc](http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc)

---

### Post by Magma828 on 2010-09-16
> **Baked- said:**
> There is a network manager addon that will manage vpnc connections for you.

I like to use the command line version and script it though as i have experienced issues with network manager.  here is some reference for you

[http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc](http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc)

Yeah I'm pretty sure that's what I'm using, because I access it from the VPN tab in Network Connections. When I click Add, I can choose between vpnc and PPTP.

Anyway, I'll see if I can get the command line version working..

---

