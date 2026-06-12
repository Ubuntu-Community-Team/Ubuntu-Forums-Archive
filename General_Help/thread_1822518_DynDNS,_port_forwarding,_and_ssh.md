---
title: "DynDNS, port forwarding, and ssh"
date: 2011-08-10
forum: General Help
---

### Post by azredwing on 2011-08-10
Hi all -

I put Ubuntu Server 11.04 on an old computer and put it on my network; I want to get dynamic DNS working to be able to ssh into that server as well as set up Subversion on it.

I configured the box to have a static IP, and it sees the internet just fine. I can ssh into it from my network.

The issue is sshing using the DDNS name - I set up DDNS correctly via my router, DynDNS website has my correct IP). Port forwarding for ssh is enabled (forwarding port 22 to the server box, for now). But I can't ssh in; just hangs.

Any ideas on what's going on?

---

### Post by kvaadithya on 2011-08-10
Did you try sshing into the box from outside your router's network?

That is, log in to a computer that is *NOT* behind your router and try sshing from that computer (using the dynamic DNS name) into the machine that is behind the router.

---

### Post by papibe on 2011-08-10
The ability to connect to a machine from your local network using its public name, or IP, is called NAT loopback (read about it [here]("http://www.dyndns.com/support/kb/loopback_connections.html")). Unfortunately most routers don't support it.

The easiest way to test your setup is to go to a Internet cafe, public library, or even better, a friend's house.

Regards.

---

### Post by azredwing on 2011-08-10
> **kvaadithya said:**
> Did you try sshing into the box from outside your router's network?

That is, log in to a computer that is *NOT* behind your router and try sshing from that computer (using the dynamic DNS name) into the machine that is behind the router.

I just ssh'd via my phone. Works okay. Thanks very much! 

Next issue, then: if I can't access the server using the DynDNS when I'm on the same network, how does this affect my ability to use svn to checkout/commit from that box both outside and inside my network?

---

### Post by kvaadithya on 2011-08-10
> 
I just ssh'd via my phone. Works okay. Thanks very much! 



You're welcome!

> 
Next issue, then: if I can't access the server using the DynDNS when I'm on the same network, how does this affect my ability to use svn to checkout/commit from that box both outside and inside my network?



Suppose you want to ssh from machine A (which is behind your router) to the server (call it machine B) which is also behind your router.

Add a line in the /etc/hosts file of machine A, as follows:

<B's static internal ip>             <B's public name>

For example, if the router has assigned the static address 192.168.1.54 to machine B, whose public name (as maintained by DynDNS) is azredwingsPC.dyndns.org, then add the following line to /etc/hosts of machine A:

192.168.1.54	azredwingsPC.dyndns.org

Do this for every machine on the internal network from which you will be sshing to B.

Now you will be able to ssh to B from inside the network, using B's public name.

Hope this helps!

---

### Post by azredwing on 2011-08-11
> **kvaadithya said:**
> You're welcome!



Suppose you want to ssh from machine A (which is behind your router) to the server (call it machine B) which is also behind your router.

Add a line in the /etc/hosts file of machine A, as follows:

<B's static internal ip>             <B's public name>

For example, if the router has assigned the static address 192.168.1.54 to machine B, whose public name (as maintained by DynDNS) is azredwingsPC.dyndns.org, then add the following line to /etc/hosts of machine A:

192.168.1.54	azredwingsPC.dyndns.org

Do this for every machine on the internal network from which you will be sshing to B.

Now you will be able to ssh to B from inside the network, using B's public name.

Hope this helps!

Perfect :) thanks again for the help!!

---

