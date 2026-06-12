---
title: "PPPoE problem"
date: 2006-01-20
forum: General Help
---

### Post by Olflo on 2006-01-20
Hi,
I have the following problem:

I configured a new PPPoE connection using pppoeconf. After answewring all the questions and giving my ISP-username and password, I can choose to trigger the connection at boot and I say yes. The script then tells me it can trigger the connection NOW and as I say yes, everything is fine, I am online.

But at the next bootup , the connection is not triggered. So I try 
pon dsl-provider 
and this gives me: 
Plugin rp-pppoe.so loaded. 
but I am NOT online.

I have to start the pppoeconf-script again and answer all the questions to go online, which is annoying.

This what my /etc/ppp/pppoe_on_boot lookes like:

#!/bin/sh

PATH=/usr/local/sbin:/usr/sbin:/sbin:/usr/local/bin:/usr/bin:/bin
export PATH

modprobe -q pppoe

exec pppd call dsl-provider

and this is the /etc/ppp/peers/dsl-provider :

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "*********"

Any ideas?

---

### Post by Parkotron on 2006-01-20
I too had this problem as well as quite a few others. In my case the problem was with /etc/network/interfaces. The solution offered in this post fixed it for me:

[http://www.ubuntuforums.org/showthread.php?t=97135#15](http://www.ubuntuforums.org/showthread.php?t=97135#15)

Hope it works for you.

---

