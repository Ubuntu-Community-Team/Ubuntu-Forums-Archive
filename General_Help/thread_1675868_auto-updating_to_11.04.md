---
title: "auto-updating to 11.04 ?"
date: 2011-01-26
forum: General Help
---

### Post by Kymus on 2011-01-26
My previous installation was old and cranky, so I reformatted and updated Ubuntu 10.10 last night. While installing RSSowl, I double checked the distribution name (by going to System > About Ubuntu) and it says 11.04 Natty Narwhal. I have no idea how that happened since all I did was do the suggested software and security updates.

Just an hour ago I did another reformat and reinstall. After everything was done, I double checked the version number upon my first login and it said 10.10. Then I go and click okay on the suggested updates and after it was maybe 75% complete, I checked the version # and it now says 11.04 *again*!

I would find it more likely that this is some sort of bug, but still, it's very strange.. Suggestions?

---

### Post by coffeecat on 2011-01-26
There is a known bug that causes the 'About Ubuntu' to tell you an updated 10.10 is 11.04 - sometimes. It hasn't affected my 10.10 - yet. :) Open a terminal and post the output of:

```
cat /etc/lsb-release 
```

That should tell you what's what.

---

### Post by Kymus on 2011-01-26
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"


Bing!

Thank you for the help :)

---

