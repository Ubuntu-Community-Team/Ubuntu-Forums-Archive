---
title: "Local subdomain problem"
date: 2010-09-10
forum: General Help
---

### Post by JasonSwett on 2010-09-10
I'm trying to set up a local subdomain and so far I've been partially successful. I've set up a local domain - gob.local - and I can access [http://gob.local/](http://gob.local/) from both my server and from other computers on my network. I'm trying to set up coupon.gob.local but I've been less successful with that.

Here's what my /etc/hosts looks like:
```

127.0.0.1       gob gob.local coupon.gob.local localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I also have a VirtualHost set up for coupon.gob.local. If I go to [http://coupon.gob.local/](http://coupon.gob.local/) in a browser on my server, it works just fine. If I go to the same URL on a different computer on my network it doesn't work. Again, [http://gob.local/](http://gob.local/) works everywhere, so I don't understand what's different about coupon.gob.local that's making it not work.

Thanks,
Jason

---

### Post by dcstar on 2010-09-11
> **JasonSwett said:**
> I'm trying to set up a local subdomain and so far I've been partially successful. I've set up a local domain - gob.local - and I can access [http://gob.local/](http://gob.local/) from both my server and from other computers on my network. I'm trying to set up coupon.gob.local but I've been less successful with that.

Here's what my /etc/hosts looks like:
```

127.0.0.1       gob gob.local coupon.gob.local localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I also have a VirtualHost set up for coupon.gob.local. If I go to [http://coupon.gob.local/](http://coupon.gob.local/) in a browser on my server, it works just fine. If I go to the same URL on a different computer on my network it doesn't work. Again, [http://gob.local/](http://gob.local/) works everywhere, so I don't understand what's different about coupon.gob.local that's making it not work.

Thanks,
Jason

If you want a DNS server then install and set up the BIND packages, otherwise add that extra domain to all the hosts files on the other PCs.

---

### Post by JasonSwett on 2010-09-13
Is there no other way? I've read that you can use /etc/avahi/hosts to accomplish this without having to modify your clients' /etc/hosts files. (I don't understand what I've read, though.)

---

