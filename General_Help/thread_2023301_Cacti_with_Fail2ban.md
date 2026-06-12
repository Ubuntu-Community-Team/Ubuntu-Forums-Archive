---
title: "Cacti with Fail2ban"
date: 2012-07-12
forum: General Help
---

### Post by matthys on 2012-07-12
Does anyone have Cacti with Fail2ban working?

I used the additional scripts from fail2ban and placed them in cacti.

/usr/share/cacti/site/scripts/fail2ban_stats.sh

The readout of the jails is done with fail2ban-client.
But as cacti is running non-root it cannot access the data.

Didn't find any solution in the forum...

What I now did was (and this works perfect):
chmod ugo+rwx /var/run/fail2ban/fail2ban.sock

But this is not really a solution, is it?

Normally you do as non-root: sudo fail2ban-client
But this is also something you do not want to do from a script.

Does anyone have a real solution for this?

---

