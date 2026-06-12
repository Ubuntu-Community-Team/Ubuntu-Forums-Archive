---
title: "Configuring CUPS Client Fallback Server"
date: 2012-07-16
forum: General Help
---

### Post by Kirk Schnable on 2012-07-16
I am currently managing a set of netbooks which can be taken home.  While they are on our premises, I manage their printers by having:

```
/etc/cups/client.conf
ServerName OUR.LOCAL.CUPS.SERVER
```

This way, they connect directly to our CUPS server while they're inside the building.  All printers are managed centrally for ease of deployment.

I want to give my end users the ability to install and manage their own printers while they're at home, essentially falling back to **localhost** as is the CUPS default.

This way, they can connect to our managed print server while they're in our building, and see and manage their personally printers while they're out of the building.

Is there an easy way within CUPS to do this?  I'd rather avoid making up a cron that replaces the configuration files, but I will resort to that if someone doesn't have a better idea.

In other words: I'm looking to setup a round-robin of servers where CUPS tries my server first, and then connects to localhost if my server is unreachable.

Thanks,
Kirk

---

### Post by Kirk Schnable on 2012-07-17
I had a thought about this yesterday.  My organization runs an internal DNS server, independent from our external DNS server.

We created a DNS record:
cups.ourdomain.org

Inside, we point it to our CUPS server, 10.9.1.122 I think.
Outside, we point it to 127.0.0.1 so they can manage their printers.

The only obvious disadvantage to this is that they won't be able to print while they're not connected to the Internet at home.

I'm not completely convinced that this is a problem. However, I'm somewhat concerned about the fact that when they go to print something, the computer might become non-responsive for a time while the DNS query is busy failing.

Anyone have any thoughts as to improvements to my approach?  If not, I'm on a timeline with this release and I'm going to test and probably release this way.

Kirk

---

