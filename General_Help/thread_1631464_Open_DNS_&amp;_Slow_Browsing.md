---
title: "Open DNS &amp; Slow Browsing"
date: 2010-11-26
forum: General Help
---

### Post by onaridge on 2010-11-26
I have looked at other threads on this subject and am still confused. Several weeks ago I had issues with browsing taking forever to resolve a page. When I changed my router to Open DNS settings that seemed to fix the slows and when I replaced the Open DNS IP's with the Google IP's, things were even quicker. Now I am back to the slows but there is no resolution latency it's just a delay when clicking a link, nothing happens and then the page eventually loads but you see the ads write on the page after the text loads. It's just not snappy. My nsswitch.config looks like this:

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

I have seen posts where they say to change the order of hosts but I only have one and it doesn't say DNS it says mdns so I am not sure how I should update this file to coincide with what I am doing in my router DNS IP settings. Can someone help me please.

---

### Post by Tobeus on 2010-11-27
Not sure how to configure the DNS on the Ubuntu side, but in the meanwhile, you may wish to see what DNS servers works best for your network.  If you can get a windows system on your network temporarily, I use [http://www.grc.com/dns/benchmark.htm]("http://www.grc.com/dns/benchmark.htm") to test which DNS servers around are the fastest and pick the top few to put into my router.

I would think that as long as you have your router configured to look at the DNS servers of your choice, and your ubuntu pointed to your router, then you shouldn't really have to do much else.  If this is running really slow, then your router may be to blame.

Either way, good luck!

---

### Post by onaridge on 2010-11-27
I have a dual boot with Windows on my laptop so I can try this there. Things are pretty speedy now that I rebooted but I might as well try this utility and get the fastest servers. Thanks a lot for the link.

---

### Post by onaridge on 2010-11-27
Ok I found this explanation of what my nsswitch file means but, my question follows at the end:

[COLOR="Red"]Name Service Switch Configuration
The order in which your system selects a method of resolving hostnames to IP addresses is controlled by the Name Service Switch (NSS) configuration file /etc/nsswitch.conf. As mentioned in the previous section,** typically static hostnames defined in the systems /etc/hosts file have precedence over names resolved from DNS.** The following is an example of the line responsible for this order of hostname lookups in the file /etc/nsswitch.conf.

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
files first tries to resolve static hostnames located in /etc/hosts.

mdns4_minimal attempts to resolve the name using Multicast DNS.

[NOTFOUND=return] means that any response of notfound by the preceeding mdns4_minimal process should be treated as authoritative and that the system should not try to continue hunting for an answer.

dns represents a legacy unicast DNS query.

mdns4 represents a Multicast DNS query.
[/COLOR]

My hosts file has this which isn't what my DNS servers are:

[COLOR="red"]127.0.0.1	localhost
127.0.1.1	loren-linux1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/COLOR][COLOR="Black"][/COLOR]

I read somewhere to disable IPv6. Should this host file not have the DNS servers I am using listed here as well as this ip6 stuff or first?

---

