---
title: "Hibernation doesn't work correctly after upgrade to Lucid"
date: 2010-05-11
forum: General Help
---

### Post by HalfWord on 2010-05-11
After the upgrade, I've noticed a problem I haven't had before - hibernating worked fine to the last. The problem is, although the system correctly hibernates, it makes no attempt to "wake" from hibernation when I power it up - it boots normally, and with fsck-ing like it was powered off without proper shutdown (understandably).

I don't know why it happens, and I've skimmed the logs, but noticed nothing special. What could be the problem? What could I try? Which log should help someone find that out?

Thank you

---

### Post by colorlessprism on 2010-05-11
i would look through the bug at launchpad. i know a number of people have been having problems with suspend/hibernate. acpi would be where i would start i guess....

---

### Post by HalfWord on 2010-05-11
Yes, I guess this is the relevant bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577916]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577916")

I can see there is an old thread here which someone revived, it seems it's the same problem...

---

