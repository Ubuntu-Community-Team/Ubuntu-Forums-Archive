---
title: "OpenVPN server won't start after reboot"
date: 2010-07-15
forum: General Help
---

### Post by TapeWorms on 2010-07-15
Hey all,

I had recently setup an OpenVPN server on x64 10.04 via the guide found at:
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
Everything was working perfectly, all clients were able to connect etc.

Today I needed to reboot for a completely unrelated issue - only to find that upon logging in, openVPN was no longer running. When I tried to execute 'sudo /etc/init.d/openvpn start' I'm presented with an interesting message...
/etc/openvpn$ sudo /etc/init.d/openvpn start
 * Starting virtual private network daemon(s)...                                 *   Autostarting VPN 'client'                                           [fail] 

This *used* to say Server. I've double checked all the configs and scripts used in the config and they all check out OK. I purged and reinstalled openVPN to no avail...

What should I be looking at/doing next?

Thanks in advance as always,

---

### Post by TapeWorms on 2010-07-16
Nobody has any ideas? :)

---

### Post by TapeWorms on 2010-07-18
Bump - Still hoping someone has an idea :)

---

