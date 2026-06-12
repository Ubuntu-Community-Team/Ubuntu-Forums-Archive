---
title: "VPN connection with DynDNS.org"
date: 2010-06-06
forum: General Help
---

### Post by Gevorg on 2010-06-06
Hi,

I just switched to Ubuntu from Win7 and want to setup VPN connection to my office network. 

On windows I was using SonicWall Global VPN client using details:

Host: <myname>.dyndns.org
User: <user>
Pass: <pass>

I read in DynDNS.com that simple VPN connection from network manager will not work here and ddclient need to be installed.

Could you please tell me how to setup VPN connection from Ubuntu?

Thank you in advance!

Best,
Gevorg

---

### Post by davidmohammed on 2010-06-06
does [this]("https://help.ubuntu.com/community/SSH_VPN") help?

---

### Post by davidmohammed on 2010-06-06
... or if you are using basic vpn - through network manager there is a vpn tab - just add and fill in the details.  What makes you think this will not work and you need some-other method to connect?

---

### Post by Gevorg on 2010-06-06
Hi,

Thank you for your feedback.

I tried VPN connection manager and added details:

Gateway: <myname>.dyndns.org
User: <user>
Pass: <pass>

And got error message that VPN connection failed.

I cannot understand reason behind :(

---

### Post by davidmohammed on 2010-06-06
hi there,
  [these guy]("http://ubuntuforums.org/showthread.php?t=1476312")s had a vpn issue which might be related to yours.  The suggested workaround was to add a manual route in the ipv4 settings tab.

---

