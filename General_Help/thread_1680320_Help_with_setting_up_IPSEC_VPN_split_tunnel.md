---
title: "Help with setting up IPSEC VPN split tunnel"
date: 2011-02-02
forum: General Help
---

### Post by gatorguy on 2011-02-02
I am running on Ubuntu 10.04 Desktop and have the "Cisco Compatible VPN (vpnc)" setup and am able to connect to my work connection when working from home. The problem I'm having is that when I connect to the work Cisco IPSEC VPN appliance from home I lose the ability to connect to the internet or any local resources on my home network.

I spoke to a colleague and he mentioned that I should setup split tunneling but unfortunately don't see that option on the "Cisco Compatible VPN (vpnc)" configuration.

Just a side note - I am able to connect via a Windows PC using the Cisco VPN client and a Mac and don't have this issue.

Thanks in advance for any assistance on configuring this.
Dan

---

### Post by gatorguy on 2011-02-02
I was able to find the fix for this. There was a post by Alienbrain that suggested making a change to the "Use this connection only for resources on its network" (see Alienbrain's post below:

Click on the Network Manager icon and choose "VPN Connections" -> "Configure
VPN...". Then choose the connection name and click "Edit". Go to "IPv4
Settings" tab and click the "Routes" button at the lower-right corner.
Check off "Use this connection only for resources on its network".

---

### Post by pbvijay on 2011-05-06
Thank you Dude... Its working fine

---

