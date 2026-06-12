---
title: "How do you roll back updates?"
date: 2010-04-06
forum: General Help
---

### Post by ngronewold on 2010-04-06
Hi guys. I'm having difficulty connecting remotely to my company's server, and I think the problem was caused by a security update sent out by Cannonical about 3 weeks ago (everything was 100% fine before then).

In Windows, the system periodically takes a snapshot of itself, keeping a record of all software and documents present at that time.  So in case new software is added that mucks up the system, a user can sort of go back in time, find a date at which everything was fine and ask the computer to restore itself to the exact condition it was at that date. New software, update packets, etc. are lost but you revert to a time when the system was healthy.

Can you do this in Ubuntu?  That way I could roll back the system to the way it was before the security update caused my issue. Otherwise I'm worried I'll have to do a fresh re-install and start from scratch.

Thanks

---

### Post by falconindy on 2010-04-06
Old packages are kept in /var/cache/apt (or maybe that's /var/apt/cache). /var/log/dpkg.log should have a nice and tidy list of what packages were upgraded, when, and the versions.

If you find that there is a package that is causing you problems, you should pin it:

```
echo "packagename hold" | sudo dpkg --set-selections
```

...and make sure to file a bug report.

---

### Post by jackhammerx on 2011-08-21
pin it? i just ran my updates last night and now my wifi wont work. it installed some new dhcp packages so im pretty sure thats the problem. i'd like to uninstall that portion of the update but im not entirely sure how to do so?

---

