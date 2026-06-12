---
title: "My PC is blocking the adobe website!"
date: 2009-10-14
forum: General Help
---

### Post by ukblacknight on 2009-10-14
Well this is a strange one.  A few months ago, I tried accessing the adobe site with no luck - it was down.  I assumed it was just a one off thing.  A while later, I tried it again, still no luck.  I clicked a link tonight to see if there is a newer version of flash - site still down!  Surely [www.adobe.com](www.adobe.com) hasn't been down for several months?!

So I ran some tests.
Target site: [www.adobe.com](www.adobe.com)

Firefox: Failed to Connect
Chromium: Oops!  This link appears to be broken.

I loaded my Ubuntu 9.10 Beta VM up, loaded Firefox 3.5:
Firefox: Failed to Connect

So I tried pinging:
```

tom@blacknight:~$ ping -c 4 www.adobe.com
PING www.wip3.adobe.com (192.150.8.60) 56(84) bytes of data.
From blacknight.local (192.168.1.2) icmp_seq=1 Destination Host Unreachable
From blacknight.local (192.168.1.2) icmp_seq=2 Destination Host Unreachable
From blacknight.local (192.168.1.2) icmp_seq=3 Destination Host Unreachable
From blacknight.local (192.168.1.2) icmp_seq=4 Destination Host Unreachable

--- www.wip3.adobe.com ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3201ms
, pipe 3


```

This got me thinking, maybe my router is some how blocking the site?  So I tried the website on my WiFi enabled phone - and the site works!

Any ideas what could be causing this?  Strange how Ubuntu, and a guest in a virtual machine can't see the site.

---

### Post by darco on 2009-10-14
Could be that your /etc/host file is blocking the site...


darco

---

### Post by ukblacknight on 2009-10-14
> **darco said:**
> Could be that your /etc/host file is blocking the site...


darco

```

tom@blacknight:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	blacknight

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

---

### Post by mac666 on 2009-10-14
but a '#' ifront of the blacknight line and restart your comp and try again.

---

### Post by ukblacknight on 2009-10-14
> **mac666 said:**
> but a '#' ifront of the blacknight line and restart your comp and try again.

Just done that, however the site is still not working.

When pinging, the address [www.adobe.com](www.adobe.com) gets resolved to '192.150.8.60' - that's a local address!  Could someone else please resolve the IP of the adobe site, and then I'll put that directly into my browser.

---

### Post by Giblet5 on 2009-10-14
+1 on that 127.0.1.1 IP address....

But commenting that out isn't likely to work...

Did you manually configure your IP address, default gateway, and DNS servers?

---

### Post by CharlesA on 2009-10-14
> **ukblacknight said:**
> Just done that, however the site is still not working.

When pinging, the address [www.adobe.com]("http://www.adobe.com") gets resolved to '192.150.8.60' - that's a local address!  Could someone else please resolve the IP of the adobe site, and then I'll put that directly into my browser.

Only 192.168.x.x is a private/local IP. That one that is being resolved points to adobe.com

---

### Post by Giblet5 on 2009-10-14
> **ukblacknight said:**
> Just done that, however the site is still not working.

When pinging, the address [www.adobe.com](www.adobe.com) gets resolved to '192.150.8.60' - that's a local address!  Could someone else please resolve the IP of the adobe site, and then I'll put that directly into my browser.

I show
adobe.com: 192.150.18.117
[www.adobe.com:](www.adobe.com:) 192.150.18.60


If your local subnet is addressed that way, you'll have ongoing trouble cuz I think Adobe owns the entire 192.150.0.0 space...

---

### Post by ukblacknight on 2009-10-14
I configured my own IP address, as my router has this habbit of re-newing our local IP's every now and again - this screws up our port-forwarding tables on the router.

Everything looks normal on the network setup for eth1 on Ubuntu.  Gateway, subnet mask etc all seem fine - I've not run into any other net problems, only this adobe site.

---

### Post by Johnny B on 2009-10-14
> **Giblet5 said:**
> 
But commenting that out isn't likely to work...


Try looking in /etc/hosts.deny
or
> cat /etc/hosts.deny | grep "192.150.8.60"

---

### Post by Giblet5 on 2009-10-14
> **CharlesA said:**
> Only 192.168.x.x is a private/local IP. That one that is being resolved points to adobe.com

+1

If you've set up a 192.150.0.0 subnet, you either need to change it 192.168.0.0 or get used to some sites being unavailable.

---

### Post by CharlesA on 2009-10-14
> **Giblet5 said:**
> +1

If you've set up a 192.150.0.0 subnet, you either need to change it 192.168.0.0 or get used to some sites being unavailable.

Looking at the IP from the ping it's set to 192.168.1.x

What's the subnet mask?

---

### Post by ukblacknight on 2009-10-14
> **Johnny B said:**
> Try looking in /etc/hosts.deny
or

I looked in there earlier when looking in /etc/hosts - that just contains the default details, all comments, no actual code.

Anyone got the IP for the adobe site I can try?

---

### Post by Giblet5 on 2009-10-14
> **ukblacknight said:**
> I configured my own IP address, as my router has this habbit of re-newing our local IP's every now and again - this screws up our port-forwarding tables on the router.

Everything looks normal on the network setup for eth1 on Ubuntu.  Gateway, subnet mask etc all seem fine - I've not run into any other net problems, only this adobe site.

What are the first two bytes of your IP? Is it 192.150?

---

### Post by ukblacknight on 2009-10-14
> **CharlesA said:**
> Looking at the IP from the ping it's set to 192.168.1.x

What's the subnet mask?

Connection information picture attached.

---

### Post by Giblet5 on 2009-10-14
> **ukblacknight said:**
> I looked in there earlier when looking in /etc/hosts - that just contains the default details, all comments, no actual code.

Anyone got the IP for the adobe site I can try?


I just posted them.

---

### Post by CharlesA on 2009-10-14
> **ukblacknight said:**
> I looked in there earlier when looking in /etc/hosts - that just contains the default details, all comments, no actual code.

Anyone got the IP for the adobe site I can try?

The correct IP is 192.150.8.60

Check yer subnet mask to ensure that is it /24.

EDIT: Subnet mask is wrong. In order to use a 192.168.x.x address, you need to use 255.255.255.0 subnet mask.

---

### Post by skillllllz on 2009-10-14
> **ukblacknight said:**
> Connection information picture attached.

Your subnet mask is wrong. Try 255.255.255.0

---

### Post by Giblet5 on 2009-10-14
> **skillllllz said:**
> Your subnet mask is wrong. Try 255.255.255.0

+1

Unless he NEEDS 24,000,000 nics on one LAN. ;)

Comforting Anecdote: Compaq's service/support center had around 5,000 PCs on one 10Mb subnet until HP took it over.

---

### Post by CharlesA on 2009-10-14
> **Giblet5 said:**
> +1

Unless he NEEDS 24,000,000 nics on one LAN. ;)

If that was the case, just go with a 10.x.x.x address. :P

---

### Post by skillllllz on 2009-10-14
> **Giblet5 said:**
> +1

Unless he NEEDS 24,000,000 nics on one LAN. ;)

LMAO, that'd be something!

---

### Post by ukblacknight on 2009-10-14
> **skillllllz said:**
> Your subnet mask is wrong. Try 255.255.255.0

This fixed it!  Cheers guys!  Amazing that I never ran into this problem before with other sites.

P.S: How do I change this thread to be "Solved"?

P.P.S: Realised how to do it.  Marked as solved :)

---

### Post by Giblet5 on 2009-10-14
> **skillllllz said:**
> LMAO, that'd be something!

5,000 PCs on one 10Mb subnet is bad enough.

Google would time out before loading and the collision LEDs on the nics were on solid.

---

### Post by Giblet5 on 2009-10-14
> **ukblacknight said:**
> This fixed it!  Cheers guys!  Amazing that I never ran into this problem before with other sites.

It only happened now because you accessed an address that appears to be inside your LAN (192.*.*.*)

With the new netmask, your local LAN is identified more uniquely as 192.168.1.*

It makes a difference.

---

### Post by skillllllz on 2009-10-14
> **Giblet5 said:**
> 5,000 PCs on one 10Mb subnet is bad enough.

Google would time out before loading and the collision LEDs on the nics were on solid.

:shock: WOW, who thought that would be a good idea?

---

### Post by KeyserSoze93 on 2009-10-14
I can access the adobe website, but I can't ping it (it seems to be blocking ping)

You could try

```
wget "http://adobe.com" -O-
```

and see what happens.

---

