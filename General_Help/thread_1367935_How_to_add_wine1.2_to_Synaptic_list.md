---
title: "How to add wine1.2 to Synaptic list?"
date: 2009-12-30
forum: General Help
---

### Post by OldGrantonian on 2009-12-30
As part of troubleshooting, I uninstalled wine1.2 using "Mark for Complete Removal" in Synaptic.

I then wanted to immediately re-install, but it was not in Synaptic.

How do I get it back in the list?

I have the "universe" repository enabled.

BTW: What's the difference between "Mark for Removal" and "Mark for Complete Removal" 
.

---

### Post by howefield on 2009-12-30
> **OldGrantonian said:**
> As part of troubleshooting, I uninstalled wine1.2 using "Mark for Complete Removal" in Synaptic.

I then wanted to immediately re-install, but it was not in Synaptic.

How do I get it back in the list?

Have you reloaded Synaptic ?

> BTW: What's the difference between "Mark for Removal" and "Mark for Complete Removal" 

Mark for Removal = takes out the packages.
Complete Removal = takes out the packages + the configuration files.

---

### Post by stew721 on 2009-12-30
> **OldGrantonian said:**
> As part of troubleshooting, I uninstalled wine1.2 using "Mark for Complete Removal" in Synaptic.

I then wanted to immediately re-install, but it was not in Synaptic.

How do I get it back in the list?

I have the "universe" repository enabled.

BTW: What's the difference between "Mark for Removal" and "Mark for Complete Removal" 
.
There is no Wine v1.2; stable is v1.0.1 and development is v1.1.35.  However, to add the Wine repo, look [here]("http://www.winehq.org/download/deb").

---

### Post by howefield on 2009-12-30
> **stew721 said:**
> There is no Wine v1.2

Just as well he isn't asking about Wine v1.2 then ;)

He is asking about Wine1.2

[http://packages.ubuntu.com/karmic/wine1.2](http://packages.ubuntu.com/karmic/wine1.2)

---

### Post by stew721 on 2009-12-30
> **howefield said:**
> Just as well he isn't asking about Wine v1.2 then ;)
Ya, I'd realized after posting that; been one of those days.  Anyhow, adding the Wine repo should hopefully help him.  Myself, I found the latest dev version to be more compatible with programs than the stable version too.  It's also proven to be more stable for me than the stable release.

---

### Post by OldGrantonian on 2009-12-31
Thanks for all the responses. Everything seems back to normal :)

I've made a note of all the bits and pieces of advice for the future. However, unfortunately, I've no idea how I repaired the damage. While using geekie commands in the terminal, I got a message saying that I had one broken package, and to use the "broken" filter to locate it.

I tried this in Synaptic, and it located wine1.2.  It had the green icon showing that it was still installed. (Strange!)

After a few random clicks, I noticed that Wine had re-appeared in the "Applications" menu, and is now working.

Next time, I'll make more notes when I'm troubleshooting. (Or did I say that in a different thread :) )

Thanks again.
.

---

