---
title: "Problems with vpn, MS-CHAP[v2] auth not performed"
date: 2005-02-22
forum: General Help
---

### Post by erygon on 2005-02-22
Hi,

I installed Ubuntu warty yesterday and it feels pretty nice distro, install was good etc, but I cannot start tunnel with pptp. Here is connection log.
```

sudo pon sauna2 debug dump logfd 2 nodetach
pppd options in effect:
debug debug				# (from command line)
nodetach				# (from command line)
logfd 2					# (from command line)
linkname sauna2				# (from /etc/ppp/peers/sauna2)
dump					# (from command line)
noauth					# (from /etc/ppp/options.pptp)
refuse-eap				# (from /etc/ppp/peers/sauna2)
name username				# (from /etc/ppp/peers/sauna2)
remotename sauna2			# (from /etc/ppp/peers/sauna2)
					# (from /etc/ppp/options.pptp)
pty pptp 10.20.30.42 --nolaunchpppd 	# (from /etc/ppp/peers/sauna2)
crtscts					# (from /etc/ppp/options)
					# (from /etc/ppp/options)
asyncmap 0				# (from /etc/ppp/options)
lcp-echo-failure 4			# (from /etc/ppp/options)
lcp-echo-interval 30			# (from /etc/ppp/options)
hide-password				# (from /etc/ppp/options)
ipparam sauna2				# (from /etc/ppp/peers/sauna2)
proxyarp				# (from /etc/ppp/options)
usepeerdns				# (from /etc/ppp/peers/sauna2)
nobsdcomp				# (from /etc/ppp/options.pptp)
nodeflate				# (from /etc/ppp/options.pptp)
require-mppe				# (from /etc/ppp/peers/sauna2)
noipx					# (from /etc/ppp/options)
using channel 32
Using interface ppp0
Connect: ppp0 <--> /dev/pts/3
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xdefeceb4> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <auth chap MD5> <magic 0x1c2189d5>]
sent [LCP ConfAck id=0x1 <auth chap MD5> <magic 0x1c2189d5>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xdefeceb4> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xdefeceb4> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xdefeceb4]
rcvd [CHAP Challenge id=0x1 <e85b8e8c5a510bbe3d61a79ced2e61f8>, name = "co7.alto.esp.fi"]
sent [CHAP Response id=0x1 <6847942ed803a2bc3e6a22e723c54d21>, name = "username"]
rcvd [LCP EchoRep id=0x0 magic=0x1c2189d5]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
MPPE required, but MS-CHAP[v2] auth not performed.
sent [LCP TermReq id=0x2 "MPPE required but not available"]
rcvd [IPCP ConfReq id=0x1 <addr 195.197.59.31>]
Discarded non-LCP packet when LCP not open
Script pptp 10.20.30.42 --nolaunchpppd  finished (pid 7926), status = 0x0
Modem hangup
Connection terminated.

```

So, mppe not available, I've heard that ubuntu kernel has mppe support and ppp_mppe module is loaded, pppd should also have support.

```

pppd --version
pppd version 2.4.2

```
```

modinfo ppp_mppe
filename:       /lib/modules/2.6.8.1-3-386/kernel/drivers/net/ppp_mppe.ko
license:        BSD without advertisement clause
vermagic:       2.6.8.1-3-386 preempt 386 gcc-3.3
depends:        ppp_generic

```
```

modprobe ppp-compress-18 && echo Working
Working

```
```

(snip from lsmod)

ppp_mppe               13056  0 
ppp_async              10624  0 
ppp_generic            27668  2 ppp_mppe,ppp_async
slhc                         7040  1 ppp_generic

```

Those seem ok to me, pptp-linux is also latest version 1.5.x something, now its only the conf files.

```

/etc/ppp/chap-secrets 
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses

# +++ pptpconfig added for tunnel sauna2
username sauna2 password *
sauna2 username password *
# --- pptpconfig added for tunnel sauna2

```
```

/etc/ppp/options.pptp 
noauth 
nobsdcomp 
nodeflate

```
```

/etc/ppp/peers/sauna2
# tunnel sauna2, written by pptpconfig $Revision: 1.2 $
# name of tunnel, used to select lines in secrets files

remotename sauna2
# name of tunnel, used to name /var/run pid file
linkname sauna2

# name of tunnel, passed to ip-up scripts
ipparam sauna2

# data stream for pppd to use
pty "pptp 10.20.30.42 --nolaunchpppd "

# domain and username, used to select lines in secrets files
name username
usepeerdns
require-mppe
refuse-eap
debug dump
# do not require the server to authenticate to our client

```
(Tested with require-mschap-v2, doesn't help)


I wanna point out that I can connect to my isps shell without any tunnel so homepna-card and drivers do work, but I just can't figure out whats wrong with this mppe thingy. Hopefully someone knows how to fix this.

If anyone cares, my connection is Saunalahti Kotikiinteä/VVO Verkko.

---

### Post by erygon on 2005-02-24
So no one really knows?

Up.

---

### Post by jstreed on 2005-03-28
I am having the exact same problem as you described.  (Exact same results as well).  All required modules are loaded and working.  I can't figure out what's wrong.  Hopefully this will be fixed soon, as I need this to work in order to get on my network here at school.  Without it, I'll have to resort to booting into windows to get my work done.

---

### Post by pwohlhart on 2005-04-18
is it possible that  **your** side is requesting mppe but your provider doesn't support it?e

at least i think the ubuntu standard-config requires mppe. 

try to remove it in /etc/ppp/pptpd-options (ie. comment require-mppe-128 )

---

### Post by jstreed on 2005-04-19
It's definitely not the configuration.  I have two computers (both Ubuntu Hoary) connecting to the same VPN.  One is a desktop, which can connect fine with the same settings.  The laptops is unable to connect with the exact same configuration.

---

### Post by erygon on 2005-06-06
Hello,

My problem was that Saunalahti doesn't use encryption any more, so removing require-mppe made things work.

Took only 5 months to figure this out. ,)

Edit:
Oh, and pwohlhart already suggested that.

---

