---
title: "Enabling IPv6 at home"
date: 2011-06-09
forum: General Help
---

### Post by Monotoko on 2011-06-09
Hi Guys, I have a server which has both IPv4 and IPv6 capabilities. My home connection only supports IPv4, and theres no plans to give us v6 any time soon.

I was wondering if I could tunnel my home computers through the server (located elsewhere), and give each computer it's own IPv6 address? If so, it needs to be cross platform as I have both Linux and Windows computers at home, any ideas? I have had a look on Google and other searches and only found linux-only solutions...

Daniel

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **Monotoko said:**
> Hi Guys, I have a server which has both IPv4 and IPv6 capabilities. My home connection only supports IPv4, and theres no plans to give us v6 any time soon.

I was wondering if I could tunnel my home computers through the server (located elsewhere), and give each computer it's own IPv6 address? If so, it needs to be cross platform as I have both Linux and Windows computers at home, any ideas? I have had a look on Google and other searches and only found linux-only solutions...

Daniel

I wouldn't do it that way.  I would buy a router that supports IPv6 and it can handle that automatically for you. :)

There may be a way of accomplishing that without a router, maybe someone here knows?

---

### Post by Monotoko on 2011-06-10
Sadly isn't an option, my ISP (who will remain anonymous) do not give out the username and password, instead they provide a router that activates automatically depending on some things...so I'm effectively locked to their router >.<

---

### Post by Monotoko on 2011-06-10
No-one has any suggestions for tunnelling?

---

### Post by lemming465 on 2011-06-10
Assuming your remote server has something bigger than a /64, it shouldn't be too hard.  As I understand it, your situation looks something like:```

home network                                            hosting provider
+============+==============+                           +============
|            |              |                           | 
|           linux          ISP router -------------   server
windows
```

Where the "+=====" networks should be dual-stack v4 + v6, but the "----" ISP uplink is IPv4 only.

This calls for your home linux box having a point-to-point link to your server, doing IPv6 forwarding, and generating IPv6 ICMPv6 Router Advertisements so that the other stuff on your home network knows there is v6 available.  This is exactly the way the experimental 6bone was built back in the late '90s before backbone ISP's supported IPv6, and yes, You Can Still Do It Today!

Surprisingly, we seem to have a lack of simple directions for setting this up.  Alas, I'm not going to fix that today :-(

You'll probably find the directions at [deepspace]("http://www.deepspace6.net/docs/iproute2tunnel-en.html") more helpful than [section 9.3 of the aging Linux IPv6 howto]("http://tldp.org/HOWTO/Linux+IPv6-HOWTO/conf-ipv6-in-ipv4-point-to-point-tunnels.html").  The most helpful thing of all may be some of the [Debian directions]("http://http://madduck.net/docs/ipv6/"), except that none of these show what the setup looks like on your server end.  For the tunnel part, and ipv6 forwarding, similar to your home linux box.  But the server end doesn't run "radvd", and needs an extra route statement to point the /64 you are advertising at home down the tunnel.

Your ISP router has to be able to pass protocol-41 (IP in IP) or maybe protocol 47 (GRE) for this kind of point to point link to work.  Don't try to use the pre-existing legacy tunnel device "sit0"; it has funky generic routing semantics you want to avoid; just add your own (virtual) tunnel device.

---

