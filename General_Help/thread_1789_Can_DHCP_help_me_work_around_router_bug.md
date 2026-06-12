---
title: "Can DHCP help me work around router bug?"
date: 2004-10-22
forum: General Help
---

### Post by cseg on 2004-10-22
I have a buggy wireless router (Netgear mr314 to be exact).  It works great most of the time.  But every once in a while it decides to stop forwarding my DNS requests.  

My DNS settings in /etc/resolv.conf are a single server at 192.168.0.1, the mr314.  Presumably this was set up by DHCP. 

When the router is in its happy state, everything is fine.  But when its mad, all DNS requests fail.  :(

I can work around this by putting some "real" DNS servers in my /etc/resolv.conf file.  This fixes the problem immediately, but only temporarily.

After a while, DHCP (?) decides that those "real" DNS servers should not be there and it resets my /etc/resolv.conf back to the "fake/broken" DNS server of 192.168.0.1.  

I can even put the "real" DNS servers via the Ubuntu GUI (Computer->Network) and they get inserted into /etc/resolv.conf.  But they always end up getting removed/replaced again later to 192.168.0.1.

Since there is no way for me to fix my router, how can I tell DHCP to stop blowing away my DNS settings???!!!  Is my buggy router in collusion with a buggy DHCP??

Thanks for any help you can give me.  This is really frustrating.

---

### Post by sfw5000 on 2004-10-22
Have you tried disabling DHCP on the network interface and manually configuring all settings? In the GUI (computer--system config--network) choose properties on your nic and set all the perameters in there... make sure you set the ip to something outside of the routers dhcp range. Like, if the router assigns 192.168.0.1-192.168.0.99 then make it something like 192.168.0.150. This has worked for me, hth.

Sam

---

