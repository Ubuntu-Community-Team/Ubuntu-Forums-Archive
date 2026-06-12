---
title: "Web site name is same as my computer name and dns points browser to local host, help."
date: 2011-05-16
forum: General Help
---

### Post by MechaMechanism on 2011-05-16
My computers name is universal-mechanism.org and my web site's name is the same thing.  I run my own DNS, Bind9.  I used to host my web site on my machine and it worked and now it's been moved to a real hosting provider and don't work.  I think my DNS is trying to send the web browser to localhost.

Bind9 recursive DNS only
Localhost name same as my domain name.
Bind sending queries to local host instead of the internet.

How do I fix this.

---

### Post by lykwydchykyn on 2011-05-16
- change your computer's name
 - Remove it's A record from bind

Problem solved, no?

---

### Post by MechaMechanism on 2011-05-16
> **lykwydchykyn said:**
> - change your computer's name
 - Remove it's A record from bind

Problem solved, no?
Nope.  My DNS is recursive only.  I always used Godaddys DNS as the authoritative name servers.  My DNS is so I don't have to use the crappy ISP DNS.

---

### Post by brntoki on 2011-05-16
Find the actual IP address of your site and bookmark that (I think IP address is what you call it).

---

### Post by MechaMechanism on 2011-05-16
> **brntoki said:**
> Find the actual IP address of your site and bookmark that (I think IP address is what you call it).
That looks like what I'm gonna have to do.

---

### Post by lykwydchykyn on 2011-05-16
What's your /etc/hosts file contain?

---

### Post by MechaMechanism on 2011-05-16
> **lykwydchykyn said:**
> What's your /etc/hosts file contain?
> 127.0.0.1    localhost
127.0.1.1    universal-mechanism.org    universal-mechanism

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allroutersCan I do this:
127.0.0.1    localhost
127.0.1.1    universal-mechanism.org    universal-mechanism
64.251.17.25 universal-mechanism.org

---

### Post by lykwydchykyn on 2011-05-16
I don't understand why you want your machine name to be the same as your website.  As long as that's the case, the *proper* behavior would be to resolve "universal-mechanism.org" to localhost.

Change the name of your machine, and update /etc/hosts accordingly.

---

