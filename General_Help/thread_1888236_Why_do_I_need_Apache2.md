---
title: "Why do I need Apache2?"
date: 2011-11-28
forum: General Help
---

### Post by hottarod on 2011-11-28
I have a linksys wireless router and my PC is connected wired to it on a 10 megabit ethernet service.  I just ordered a PS3 which I plan to use to access the net through the wireless router.

Do I need Apache2 for this set up?  Why is it now installed with Ubuntu?  Since it is running do I have a hole in my system security that somebody can get through via Apache2 and if so how do I plug the hole? 

I'm running Ubuntu 11.10 with Firefox 8, current updates.

---

### Post by Dangertux on 2011-11-28
> **hottarod said:**
> I have a linksys wireless router and my PC is connected wired to it on a 10 megabit ethernet service.  I just ordered a PS3 which I plan to use to access the net through the wireless router.

Do I need Apache2 for this set up?  Why is it now installed with Ubuntu?  Since it is running do I have a hole in my system security that somebody can get through via Apache2 and if so how do I plug the hole? 

I'm running Ubuntu 11.10 with Firefox 8, current updates.

You shouldn't need Apache 2, as for why you have it installed, did you install it? It doesn't install by default.

As far as being a security threat, while the Apache folks are pretty quick at fixing up holes, running any unnecessary service is a liability.

You can remove apache by doing the following

```

sudo apt-get remove --purge apache2

```

---

### Post by hottarod on 2011-12-02
Thanks.  I did not install it.  It appears to have come down with Linux 11.10.  There is a bunch of other apache related utilities and libraries left behind even with apache2 un-installed.

---

