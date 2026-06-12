---
title: "openvpn configuration file enabling TCP and UDP?"
date: 2009-12-03
forum: General Help
---

### Post by linux000019 on 2009-12-03
**what would the config file look like if i wanted tcp and upd both enabled?** 

this is the config as it is now, setup for tcp. i want to enable tcp and upd on the same port, 443.
 
openvpn --mktun --dev tap0 
brctl addif br0 tap0 
ifconfig tap0 0.0.0.0 promisc up 
echo " 
 
-----BEGIN OpenVPN Static key V1----- 
i obv edited my key out 
-----end static key------------------ 
 
" > /tmp/static.key 
ln -s /usr/sbin/openvpn /tmp/myvpn 
/tmp/myvpn --dev tap0 --secret /tmp/static.key --comp-lzo --port 443 --proto tcp-server --verb 3 --daemon

---

### Post by linux000019 on 2009-12-03
if i add a --proto upd --proto tcp-server 

will that work? can i define two protos in the same config file?

---

