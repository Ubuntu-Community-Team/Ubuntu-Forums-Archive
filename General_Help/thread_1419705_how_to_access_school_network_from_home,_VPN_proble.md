---
title: "how to access school network from home, VPN problem?"
date: 2010-03-02
forum: General Help
---

### Post by xingerguan on 2010-03-02
When I used windows, I downloaded VPN from school and installed it onto my desktop at home so that I can access school's resource.
Now I'm using Ubuntu, and there's no such a VPN to download from school, what can I do?

---

### Post by thebigob on 2010-03-02
If it is a cisco vpn then you can simply install the vpnc plugin for network manager:

sudo apt-get install network-manager-vpnc

then add the vpn in the networkmanager.

---

### Post by xingerguan on 2010-03-02
It's Juniper NetWorks, not Cisco. In the windows system, it stresses I need to uninstall the Cisco system first to make the Juniper work.

---

### Post by thebigob on 2010-03-15
> **xingerguan said:**
> It's Juniper NetWorks, not Cisco. In the windows system, it stresses I need to uninstall the Cisco system first to make the Juniper work.

You could give [this]("http://www.ubuntugeek.com/howto-setup-juniper-network-connect-vpn-on-ubuntu-9-10.html") a shot?

---

