---
title: "Trouble getting Openswan IPsec working"
date: 2012-08-20
forum: General Help
---

### Post by Shadyjames on 2012-08-20
Okay so i'm trying to set up an ipsec vpn, so i installed openswan, which didn't immediately work, as in it didn't come up in the network managers list of vpn types. Which is fair enough, so i did "ipsec verify" to see what the problem was, and got the following output: 

```
Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                             	[OK]
Linux Openswan U2.6.37/K3.2.0-29-generic (netkey)
Checking for IPsec support in kernel                        	[OK]
 SAref kernel support                                       	[N/A]
 NETKEY:  Testing XFRM related proc values                  	[FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/send_redirects
  or NETKEY will cause the sending of bogus ICMP redirects!

	[FAILED]

<truncated, the remaining tests were all fine>

```

So i started solving one problem, as one does. I did as it asked and set the value of all the /proc/sys/net/ipv4/conf/*/send_redirects files to 0, and ran ipsec verify again, to get THIS output, which both blew my mind, and i am almost certain is the result of a bug:

```
Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                             	[OK]
Linux Openswan U2.6.37/K3.2.0-29-generic (netkey)
Checking for IPsec support in kernel                        	[OK]
 SAref kernel support                                       	[N/A]
 NETKEY:  Testing XFRM related proc values                  	[OK]
	[FAILED]

```

Whats caught my eye is that theres one more result than there are tests. Namely, the test that should now be passing has now disappeared from the list, replaced with a "[FAILED]" and the test before it is inexplicably passing now (Which i do not actually believe for a moment, i am assuming for the moment this is a false positive), even though i don't even know what XFRM is.

So yeah, two main things:
One, is what i described a bug, and should i be reporting that to openswan?
And two, somebody please help me fix my IPsec! I've never used a vpn before so most of this terminology is new to me, but i'm pretty sure i'm a non-retard, so i should be able to follow any sufficiently unambiguous instructions.

---

