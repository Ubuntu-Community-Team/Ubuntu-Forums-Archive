---
title: "script help with openvpn and huludesktop"
date: 2010-03-14
forum: General Help
---

### Post by jonjo on 2010-03-14
Hi,
I'm trying to get my US openvpn to start before opening huludesktop. I can start my vpn from the command line:


sudo openvpn --cd /etc/openvpn --config client.ovpn

but if I put in a script vpnhulu.sh

#!/bin/bash
sudo openvpn --cd /etc/openvpn --config client.ovpn &
huludesktop %F

It doesn't work - huludesktop starts but the vpn client doesn't start

I need help! Thanks!!

---

### Post by jonjo on 2010-03-14
Ok so I got it working with

#!/bin/bash
cd /etc/openvpn
sudo openvpn --config client.ovpn &
sleep 15
huludesktop %F
sudo killall openvpn
exit

BUT it doesn't exit properly when I close huludesktop. It kills the openvpn process but doesn't exit the terminal window

Any ideas? Thanks :)

---

