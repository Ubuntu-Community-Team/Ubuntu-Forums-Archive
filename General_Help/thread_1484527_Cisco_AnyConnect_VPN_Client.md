---
title: "Cisco AnyConnect VPN Client"
date: 2010-05-15
forum: General Help
---

### Post by oakdeveloper on 2010-05-15
Hi,

I need Cisco AnyConnect VPN client for Ubuntu. Where can I download it? Please give me the link.

Thanks,
Babu

---

### Post by dwmw2 on 2010-05-24
Ubuntu contains a client for Cisco AnyConnect. Just install the openconnect and network-manager-openconnect packages.

---

### Post by oakdeveloper on 2010-05-24
> **dwmw2 said:**
> Ubuntu contains a client for Cisco AnyConnect. Just install the openconnect and network-manager-openconnect packages.

Thanks a lot! I have installed those packages now. I ran the command "sudo openconnect <ipaddress>" and it asked me for my username and password. But then I got a message saying "DTLS handshake failed:2". Any idea what this means? I am stumped.

Regards,
Babu

---

### Post by dwmw2 on 2010-05-25
Sounds like you're connected. But if you're using it from the command line, perhaps you needed to give it an argument like '--script /etc/vpnc/vpnc-script' so that it can use that script to set up the routing and DNS properly?

Ignore the DTLS warnings. You're probably just behind NAT or something horrid like that instead of being connected properly to the Internet. You're still connected; just over TCP instead of UDP. It's not as good, but it should work.

The OpenConnect web page at [http://www.infradead.org/openconnect.html](http://www.infradead.org/openconnect.html) covers both of these topics.

---

### Post by oakdeveloper on 2010-05-26
Thanks so much! I got my VPN connection to work perfectly now.

---

### Post by Marc van der Wijst on 2011-02-14
Solution still worked for me. Thanks!

Installed "openconnect" and "vpnc" and made a very tiny bash script.
Just call me lazy... :mrgreen:
```

#!/bin/bash
gnome-terminal -x sudo openconnect IPHERE --script /etc/vpnc/vpnc-script

```

---

### Post by almikul on 2012-04-17
> **Marc van der Wijst said:**
> Installed "openconnect" and "vpnc" and made a very tiny bash script.
```

#!/bin/bash
gnome-terminal -x sudo openconnect IPHERE --script /etc/vpnc/vpnc-script

```
Thanks! The script fixed the DNS problem for me. 

By the way, this vpnc script should remain in its default location (i.e., in /etc/vpnc/); otherwise, it will not work properly.

---

### Post by oldos2er on 2012-04-17
Closed, necromancy.

---

