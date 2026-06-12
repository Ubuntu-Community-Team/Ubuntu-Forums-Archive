---
title: "Telnet session hanging on Ubuntu 9.04"
date: 2010-04-25
forum: General Help
---

### Post by aghufran on 2010-04-25
Hello,

I am running Ubuntu 9.04 on a wireless networked host machine. The wireless NIC is usb based. Its running inetd for network based servers (telnet, ftp etc).

For some reason telnet, ssh or any application specific connection, hangs for a few seconds and then comes back. This happens after every few minutes. I do not loose any sessions or any data flowing across but it is sort of very annoying.

It is a dual boot machine and I have also got Windows XP 64-bit. When am running on windows this does not happen, hence am not sure if it is something to do with the wirless nic or something else.

Any help would be most appreciated.

Thanks and regards,

Abid Ghufran.

---

### Post by blueridgedog on 2010-04-25
When I am trouble shooting such things, I usually resort to tcpdump on either the host or the server system.  If you open a second window and dump packets to or from the remote system, you may get an idea of what is happening during the lag.

---

### Post by efflandt on 2010-04-26
Check to make sure that your wireless device is not using any energy saving mode that might put it to sleep when temporarily inactive.

Also if you have SSID broadcast disabled on your wireless router, that really does not help security any (SSID is revealed in the clear in any traffic), and can result in interruptions when wireless devices cannot tell if the AP is still active until there is traffic.

Not sure if DNS is an issue, because inetd tries to resolve any connecting IP to a name (for checking hosts.allow and hosts.deny).  But I think that would only cause lag on initial connection, and not after connection is established.

For security reasons, I usually use ssh and scp, even locally, with **KeepAlive yes** in the default **Host *** of my ~/.ssh/config because the wireless on my DSL modem/router only does 64(40) bit WEP (but it is in the basement, so range beyond my home is limited).

---

