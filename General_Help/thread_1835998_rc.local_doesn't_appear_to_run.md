---
title: "rc.local doesn't appear to run"
date: 2011-08-30
forum: General Help
---

### Post by TheodoreWard on 2011-08-30
For years I have used fwbuilder to maintain my firewall and I run the script from rc.local.
Since 11.04 came out, the firewall will not start. I'm not sure if /etc/rc.local isn't executing or if its a problem with the rules being overwritten somehow or what...

I tried at some point to get the script to function as an upstart script, and it seemed to be added in all the proper places, but didn't seem to run. I have even tried adding it as startup application from the menu, still no iptables loaded after boot.

If I run the script manually after booting everything is fine. Any ideas what is happening here?

Maybe UFW is flushing my rules (even though I haven't configured UFW in any way)

Thanks,
Ted Ward

---

