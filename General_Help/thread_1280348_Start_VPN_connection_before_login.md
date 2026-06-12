---
title: "Start VPN connection before login"
date: 2009-10-01
forum: General Help
---

### Post by evolutionspeak on 2009-10-01
Does anyone know a way to start VPN connections on boot without requiring anyone to be logged in?

I tried starting vpnc using an init.d script, but that seems to fail because NetworkManager hasn't started the network connections yet.  I turned the /etc/init.d/vpnc script on by doing "sudo update-rc.d vpnc defaults 51 49".  The NetworkManager script starts at 50, so that command should make it start after the NetworkManager and be shutdown before it.  

But I think the NetworkManager script starts and returns before the network connections are actually made.

Anyone have any ideas, or where I should actually be asking this?  Thanks.

---

### Post by evolutionspeak on 2009-10-02
Someone must at least know who I could ask.

---

