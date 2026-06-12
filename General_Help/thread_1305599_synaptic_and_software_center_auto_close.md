---
title: "synaptic and software center auto close"
date: 2009-10-30
forum: General Help
---

### Post by mCion on 2009-10-30
I remember I had this problem before, however I cant find the answer..

Anytime I run the software center or the Synaptic, it opens and closes automatically

I recall I had to type something in the terminal to get it working, something like cleaning a cache.....but I dont remember..

help anyone?

---

### Post by mCion on 2009-10-30
This has been an interesting start.  Apparently it fixed itself, beats me what happened.

Besides getting some "serious kernel errors" everything else seems to be working fine.

Thanks!

---

### Post by artmendez on 2011-11-02
I am currently facing the same problem running 11.10 64-bit.

Synaptic used to work ok until last week. I just noticed Software Center did the same thing... but after trying a couple times it worked back. But the same thing happened some days ago with Synaptic Package Manager...

I found your question and you might ask about doing:

```
sudo rm -rf /var/cache/apt/*.bin
```

which flushes apt's cache.

Then do:

```
sudo apt-get update
 sudo apt-get upgrade
```

This will rebuild the cache.

BTW... I've not fixed my problem yet. :)  HAHA!

... and anyway... I don't really expect (and hope) you are still having this problem...

Best regards.


A.

---

