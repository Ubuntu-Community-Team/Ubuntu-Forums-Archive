---
title: "Stateless DHCPv6: how to create your own IPv6 address"
date: 2012-02-22
forum: General Help
---

### Post by sanderj on 2012-02-22
Hi, a question on IPv6 and stateless DHCPv6:

My ISP provides IPv6. The devices on my LAN get their IPv6 addresses via "stateless DHCPv6" from the modem/router connected to my ISP. Typical addresses are like 2a00:cd8:c3f1:abcd:1234:1696:6393:8285/64. These IPv6 addresses are dynamic; they have a certain lifetime, and then change.

What I want is a fixed IPv6 address on the servers on my LAN, and preferrably a short IPv6 address, so something like 2a00:cd8:c3f1:abcd::1/64.

As it is Stateless DHCPv6, I'm quite sure the DHCPv6-server (=modem) only sends the IPv6-prefix, and the client makes up the right part. How can I instruct the client to just put a "::1" on the right side? I googled, and couldn't find a solution.

Tips appreciated

---

### Post by Khayyam on 2012-02-22
> **sanderj said:**
> As it is Stateless DHCPv6, I'm quite sure the DHCPv6-server (=modem) only sends the IPv6-prefix, and the client makes up the right part. How can I instruct the client to just put a "::1" on the right side? I googled, and couldn't find a solution.

sanderj ... I've very little experience with IPv6, what I know mostly coming from reading rather than implimentation. However, I was under the impression that with "stateless" "IPv6 prefix" is provided by the client as part of "autoconfiguration", the DHCPv6 mearly providiing DNS server, and domain. I could be wrong in this regard, but I thought that the autoconfiguration was the whole point of it being 'stateless'.

Its been a while since I've read anything on the subject, so forgive my, real or apparent, ignorance, but isn't it a simple matter of the client running 'dhclient -S' to be 'stateless'?

HTH in some way ... khay

---

### Post by sanderj on 2012-02-22
> **sanderj said:**
> Hi, a question on IPv6 and stateless DHCPv6:

My ISP provides IPv6. The devices on my LAN get their IPv6 addresses via "stateless DHCPv6" from the modem/router connected to my ISP. Typical addresses are like 2a00:cd8:c3f1:abcd:1234:1696:6393:8285/64. These IPv6 addresses are dynamic; they have a certain lifetime, and then change.

What I want is a fixed IPv6 address on the servers on my LAN, and preferrably a short IPv6 address, so something like 2a00:cd8:c3f1:abcd::1/64.

As it is Stateless DHCPv6, I'm quite sure the DHCPv6-server (=modem) only sends the IPv6-prefix, and the client makes up the right part. How can I instruct the client to just put a "::1" on the right side? I googled, and couldn't find a solution.

Tips appreciated

Well, I would say the client really needs to get the prefix (the left part) from a central system. In case of Router Advertisment (RADVD) I have experience that the RADVD advertises the prefix. And AFAIK with stateless DHCP it works the same way: the prefix is in the DHCP-response, just like the nameserver etc.

So I want to instruct my client: "get the prefix, and just put ::1 on the righ side" ...

---

### Post by lemming465 on 2012-02-23
Oooh, a tough one.  I don't think this case - dynamic prefix, static host part - is really well covered by the existing Linux code, or for that matter the RFC's defining IPv6.  Statically configured hosts have complete control over their host parts, of course, but are expecting a fixed subnet prefix too.  Dynamically configured hosts have a couple of different strategies for picking addresses, but not this one.  So you are going to have to resort to some scripting to implement it.

To recap for the uninitiated who might be reading this thread, in IPv6 routers are required to send ICMPv6 "router advertisement" messages (type 134, RFC4861).  RA's existed in IPv4, but no one ever used them :-( Oversimplifying a bit, there are 3 major components of interest in IPv6 RA's:
  (1) the link-local scope (fe80::/64 prefix) IPv6 address of the router
  (2) flag bits, particularly M ("managed") and O ("other")
  (3) a list of on-link prefixes

When a host brings up IPv6 on an interface, it normally listens for RA's, and usually multicasts a router solicitation (ICMPv6 type 133, destination ff02::2) to provoke one.  The M and O flags control the the DHCPv6 behaviours.  If the M flag is off, you are in the stateless autoconfiguration case ("SLAAC"), and for each on-link prefix you received from the routers, you self-generate a host part using some strategy you like, and paste them together to get one of your many IPv6 addresses.  If the M flag is on, you get your addresses from your DHCPv6 server.  Meanwhile, if the O flag is on, whether or not you are doing SLAAC, you are doing DHCPv6 anyway, to get optional information such as your DNS prefix, DNS servers, etc.  What a host might do in the face of conflicts between DHCPv4 and DHCPv6 is undefined, so most production v6 networks at the moment use SLAAC for the v6 addresses and gateways, and DHCPv4 for everything else.  Note that DHCPv6 has no gateway options, so the only way to find your IPv6 gateways is to listen to the RA's.

There are two main strategies for picking self-generated host-parts to combine with advertised prefixes in SLAAC: EUI-64 mapping, and privacy.  In the EUI-64 case you take your 48-bit ethernet MAC, stuff "fffe" in the middle, and flip the U/L bit.  In the privacy case you pick 62 of the 64 host part bits at random (the local flag bit and multicast flag bit are fixed). Linux, Cisco, and Apple do the former by default, Microsoft the latter.  Your Linux choice is controlled by your sysctl setting for "use_tempaddr", which can be things like 0=disable privacy, 1=allow privacy, 2=prefer privacy.

Back at sanderj's case, where he wants an upstream dynamic prefix with a static host part, this is not one of the standard optinos. So maybe he tries a strategy like:

(1) install the ndisc6 package

(2) in /etc/network/interfaces, specify something like ```

auto eth0
iface eth0 inet6 manual
  up /my/up/script
  down /my/down/script
```

(3) in /my/up/script parse the output of "rdisc6 -1 -q eth0" to find out the prefix and gateway

(4) run ip commands using the data from (3) to set the address and route by hand
     ip -6 addr add ... dev eth0
     ip -6 route add ...

---

### Post by sanderj on 2012-02-24
@lemming465:

Thank you. That helps me. And: this is something that is NOT implemented in the dhcpv6 client? I would think it is a quite regular requirement, and had hoped is was just an option in the dhcp configuration...

Do you know when /etc/network/interfaces is run? 

rdisc6 is very useful:
```

$ rdisc6 -1 -q wlan1
2a00:cd8:abcd:1234::/64


```

I had already written a working one-liner to add a random postfix/right part to the IPv6 address:

```

#!/bin/bash

ip -6 addr add 2a00:cd8:AABB:CCDD:`date +%j:%k%M`:$[$RANDOM % 10000]:2222/64 dev wlan0    valid_lft 28800 preferred_lft  14400


```


The problem with this script is when to run it: certainly each time the interface goes up. And of course I should add a few checks to it.

And I had written a bit more clever python script 

```

import os, string, random
from time import strftime, localtime

interfacecounter = 0
cmd = 'ip -o -6 addr show  |  grep -i dynamic'
for thisline in os.popen(cmd).readlines():
	'''
	3: wlan1    inet6 2a00:cd8:aabb:ccdd:224:2cff:fe6a:54ab/64 scope global dynamic \       valid_lft 2591897sec preferred_lft 604697sec
	'''
        interfacecounter += 1
        # dimmtotal += int(thisline.split()[1])
	interface = thisline.split()[1]
	address = thisline.split()[3].split('/')[0] 
	prefixlength = int(thisline.split()[3].split('/')[1])
	(address,prefixlength)=thisline.split()[3].split('/')
	prefixlength = int(prefixlength)
	print address, prefixlength, interface

	'''
	If there is an '::' in address, replace it with the neede ':0:0:...' so that the number of blocks is 8
	2001::1 should turn into 2001:0:0:0:0:0:0:1
	2001::a:1 should turn into 2001:0:0:0:0:0:a:1
	2001:1234:: should turn into 2011:1234:0:0:0:0:0:0
	'''
	# address = '2001:abcd::1'
	fulladdress = address
	if address.find('::') > -1:
		# Yep, a :: found, so fill out with :0:'s
		# 2001:abcd::1 has 4 blocks
		fill = 9 - len(address.split(':'))	# 9 - nummbers of blocks
		(leftpart,rightpart) = address.split('::')
		if rightpart == '':
			rightpart = '0'
		fulladdress = leftpart + ':0'*fill + ':' + rightpart
		print fulladdress


	prefixblocks = prefixlength / 16	# to do: what if prefix is not multiple of 16?!
	prefix = string.join(fulladdress.split(':')[0:prefixblocks],':')
	print prefix

	print str(hex(random.randint(1, 65535))[2:])

	'''
	ip -6 addr add 2a00:cd8:XXYY:PPQQ:`date +%j:%k%M`:$[$RANDOM % 10000]:2222/64 dev wlan0    valid_lft 28800 preferred_lft  14400

	'''
	dayofyear = strftime("%j", localtime())
	timething = strftime("%H%M", localtime())
	randomhex = hex(random.randint(1, 65535))[2:]
	postfix = ('0','0','0','0',dayofyear,timething,'cafe',randomhex)

	newaddress = string.join(fulladdress.split(':')[0:prefixblocks],':') + ':' + string.join(postfix[prefixblocks:8],':')
	print newaddress

	cmd = 'ip -6 addr add ' + newaddress + '/' + str(prefixlength) + ' dev ' + interface + '   valid_lft 28800 preferred_lft  14400'
	print cmd
	for resultline in os.popen(cmd).readlines():
		print resultline

	cmd = 'ip -6 addr show | grep ' + newaddress
	for resultline in os.popen(cmd).readlines():
		print resultline


print "Finished"


```

with really works, with the following output

```
$ sudo python ipv6-dhcp.py 
2a00:cd8:aaaa:c11e:55:811:cafe:a3d1 64 wlan1
2a00:cd8:aaaa:c11e
b4be
2a00:cd8:aaaa:c11e:055:0813:cafe:9cf0
ip -6 addr add 2a00:cd8:aaaa:c11e:055:0813:cafe:9cf0/64 dev wlan1   valid_lft 28800 preferred_lft  14400

```

Hopefully I can combine things to get a reliable solution.

---

