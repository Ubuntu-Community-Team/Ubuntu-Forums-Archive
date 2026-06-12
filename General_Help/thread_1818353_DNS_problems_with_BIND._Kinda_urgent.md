---
title: "DNS problems with BIND. Kinda urgent"
date: 2011-08-04
forum: General Help
---

### Post by SloS13 on 2011-08-04
I'm a linux noob so please bear with me.  I'm supposed to have this server in a production environment by tomorrow.  I've been pulling my hair out but I think I've met my match.

I've got an Ubuntu 10.04 running BIND and am configuring it through Webmin.  I've got several domains set up and they work fine.  I've got the google's 8.8.8.8,.4.4 set up as the forwarders and am able to ping my domains as well as outside domains, so that's working great.

*note: In the setup for the linux networking adapter, I have 127.0.0.1 for the DNS server so it's using itself for DNS.

For testing, I hooked up a laptop and set it up to use the new server for DNS.  The laptop can ping/resolve the domains set up in BIND but not other domains for some reason.

I have Firestarter installed but turned off for troubleshooting purposes.

Thanks in advance for any advice!

---

### Post by idlemind324 on 2011-08-04
For testing your DNS service I strongly recommend using the dig @<ip addr> command. It will then issue just DNS commands to your test server.

Also when you setup your forwarders do they look something like:

forwarders {
[INDENT][INDENT]8.8.4.4;[/INDENT][/INDENT]
[INDENT][INDENT]8.8.8.8;[/INDENT][/INDENT]
};

in the file /etc/bind/named.conf.options

Have you restarted the bind service to be sure that those forwarders were applied?

---

### Post by SloS13 on 2011-08-04
> **idlemind324 said:**
> For testing your DNS service I strongly recommend using the dig @<ip addr> command. It will then issue just DNS commands to your test server.

Thank you kindly for your help but I *just* figured it out. I feel like the awesomest person in the universe.

I was missing this from /etc/bind/named.conf.options

```
allow-recursion { any; };
allow-recursion-on { any; };
```

---

