---
title: "Bind Name Caching Server"
date: 2011-02-22
forum: General Help
---

### Post by sandkernel on 2011-02-22
Hi all,

Quick one for the Bind experts out there. I've set up a Bind name caching server for my small internal network. Pretty much have everything working. I am curious about one thing however. When I do a dig cnn.com for instance I get the time as around 50 msec. If I do it again immediately it is (as I would expect) around 1 msec. If I wait a few minutes then it goes back to 50 msec.

So to the untrained eye (me) I think "ok, so the cache has expired". Where do I tweak that? I don't see the benefit with the settings as they are. I want the names to stay in the cache a little longer than what the setting is now.

thanks

---

