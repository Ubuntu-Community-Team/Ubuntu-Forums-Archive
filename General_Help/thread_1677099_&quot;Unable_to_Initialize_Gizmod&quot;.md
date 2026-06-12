---
title: "&quot;Unable to Initialize Gizmod&quot;"
date: 2011-01-28
forum: General Help
---

### Post by ninjaaron on 2011-01-28
Hey, I just install GizmoDaemon.

When I attempt to run the program it outputs:
```

GizmoDaemon v3.4 -=- (c) 2007, Tim Burrell <tim.burrell@gmail.com>
=---------=

Unable to Initialize Gizmod :: User Script dir [/usr/etc/gizmod/modules.d] does NOT exist or permissions are wrong!

GizmoDaemon Shut Down.

```

So now what?

---

### Post by disc9 on 2012-09-15
Same problem on Ubuntu 11.04 was fixed by:
Copying the contents of /etc/gizmod/ into /usr/etc/gizmod/

---

