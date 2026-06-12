---
title: "Routine &quot;admin&quot; email... what should I expect/how to enable?"
date: 2009-06-25
forum: General Help
---

### Post by nemein on 2009-06-25
I just set up my first ubuntu server :D  However it occurred to me that up until now I've only run ubuntu on laptops (which don't stay up and running all the time) on machines that were "disposable" (don't really care if they go belly up as they aren't doing anything critical).  Since I need the machine to stay up and running I would like a little more feedback from it. On the BSD, RH and Sun machines I've dealt w/ in the past there are a slew of routine/admin messages that get mailed (at least every night), but so far I haven't seen anything like that from my new server.  I know mail works and messages mailed to root are sent to the proper alias used by all the machines on the network  so that's not the issue.  Is there something I need to do to enable these?  In particular I enabled the automatic updates and I would like feedback when that happens (and hopefully a record of the changes made).

BTW a command line option/way of doing this would be preferred.  I did install a desktop but it is easier to login to the machine remotely and do any sort of admin that way.

Any hints/clues/suggestions would be appreciated.
TIA

---

### Post by dcstar on 2009-06-26
> **nemein said:**
> I just set up my first ubuntu server :D  However it occurred to me that up until now I've only run ubuntu on laptops (which don't stay up and running all the time) on machines that were "disposable" (don't really care if they go belly up as they aren't doing anything critical).  Since I need the machine to stay up and running I would like a little more feedback from it. On the BSD, RH and Sun machines I've dealt w/ in the past there are a slew of routine/admin messages that get mailed (at least every night), but so far I haven't seen anything like that from my new server.  I know mail works and messages mailed to root are sent to the proper alias used by all the machines on the network  so that's not the issue.  Is there something I need to do to enable these?  In particular I enabled the automatic updates and I would like feedback when that happens (and hopefully a record of the changes made).

BTW a command line option/way of doing this would be preferred.  I did install a desktop but it is easier to login to the machine remotely and do any sort of admin that way.

Any hints/clues/suggestions would be appreciated.
TIA

```
man logcheck
```

---

### Post by nemein on 2009-06-26
$ man logcheck
No manual entry for logcheck

Did a default install so I'm not sure why it isn't there...

Ok I see it's a package that can be installed/not installed by default.  I'll check it out and see if that gives me what I'm looking for.  Is this something like RH's "logwatch" email?

---

