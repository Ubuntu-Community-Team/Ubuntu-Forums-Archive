---
title: "Help: LTSP + Logkeys"
date: 2012-03-13
forum: General Help
---

### Post by Islander2010 on 2012-03-13
Hello,

I'm not really sure where to post this, so I hope this is the right place.

We are currently using Ubuntu 10.04 and LTSP5 environment. I'd like to use the logkeys application to log user activity on our thin clients. Does anybody know how to achieve this?

I've tried running it on the server but it seems to capture only keystrokes coming from the keyboard connected to the server. The only other way I see it is to run it from the thin client via localapps. However, when I chroot to the ltsp image and try to configure/build the logkeys app it can't find the input devices (naturally) and therefore it does not continue.

Any ideas on how to achieve this?

---

