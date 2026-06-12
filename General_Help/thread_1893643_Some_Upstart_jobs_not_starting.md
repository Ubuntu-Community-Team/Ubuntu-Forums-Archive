---
title: "Some Upstart jobs not starting?"
date: 2011-12-10
forum: General Help
---

### Post by csete on 2011-12-10
Ever since I upgraded to 11.10, I've noticed some jobs that aren't starting automatically on my server machine when I would expect them to start up.  I'm not entirely sure what might be going on and could use some help.  I've seen this behavior for SMBD and Mediatomb.  In both cases, the upstart configuration is based on filesystem and network connections:

start on (local-filesystems and net-device-up IFACE!=lo)

I hacked up SMBD as follows and it works consistently now, but it doesn't seem like it should be necessary:

start on filesystem or runlevel [2345]

Even though this is a "server" machine, I'm currently using network-manager to configure my networking.  Might this have something to do with things not autostarting?  Should I swap out network-manager for ifupdown?

Thanks,
Craig

---

