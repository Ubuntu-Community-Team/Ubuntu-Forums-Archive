---
title: "ltspfs mount permission denied"
date: 2012-04-21
forum: General Help
---

### Post by davidgempton on 2012-04-21
I've just spent quite a lot of time trying to figure out why the usbsticks were not mounting and showing up on the ltsp client desktops.

In my case the issue was the ownership of the users directory under /media on the ltsp server.

For some reason my users directory under /media was owned by another user.

Setting the ownership with chown <user_name> /media/<user_name> fixed the issue.

Hope someone else finds this helpful.

---

