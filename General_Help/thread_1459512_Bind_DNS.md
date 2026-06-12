---
title: "Bind DNS"
date: 2010-04-21
forum: General Help
---

### Post by sr_guy on 2010-04-21
I have bind installed and setup on my Jaunty box. I have the IP of the machine hardcoded in my router as a static DNS. The other two static dns's in the router populate with my ISP's DNS servers. How do I test to make sure dns is being pulled by my local machine?

---

### Post by andrewc6l on 2010-04-22
I'm not 100% sure I understand your question, so my apologies if this isn't the answer you're looking for.

If you want to make sure you're talking to the DNS server on your box, run nslookup and enter 'server'. The default server it finds should be yours:

$ nslookup
> server
Default Server:  192.168.1.1
Address:  192.168.1.1#53

If your router is acting as DNS and getting addresses from your Linux box, you'll see the router address. 

The simplest way to make sure you're using your DNS in that case is to add a name/IP to that DNS (that you're pretty sure doesn't exist elsewhere) and try to resolve it. If you add 'mysecretdnsmachinename.com' as 192.168.1.2 and then nslookup mysecretdnsmachinename.com. 

If it resolves to what you expect, you're good. If it resolves to nothing, you know your DNS server isn't being consulted. If it resolves to some random IP, you know your ISP is redirecting failed lookups :-(

---

### Post by dcstar on 2010-04-22
> **andrewc6l said:**
> 
.......
If it resolves to what you expect, you're good. If it resolves to nothing, you know your DNS server isn't being consulted. If it resolves to some random IP, you know your ISP is redirecting failed lookups :-(

DNS lookups have absolutely nothing to do with your ISP unless **you** make it so by using an ISP DNS server as a forwarder (which is basically a common-sense thing to do anyway for external queries).

Unless you are hosting a Domain's DNS entries or multiple PCs in your internal network there is little point in setting up a DNS server.

---

