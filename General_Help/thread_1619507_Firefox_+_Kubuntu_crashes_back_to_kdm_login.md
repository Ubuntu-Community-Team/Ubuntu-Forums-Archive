---
title: "Firefox + Kubuntu crashes back to kdm login"
date: 2010-11-11
forum: General Help
---

### Post by yuki-nagato on 2010-11-11
Since I upgraded to Maverick, I noticed that Kubuntu would crash back to the kdm login or lock up entirely with even the magic syskey (alt printscreen REISUB ) not working and at first I didn't really connect the dots as to what was causing this until recently...  It turns out that this pretty much only happens in Firefox with Noscript enabled during certain times- pretty random in when it happens but it tends to happen more often the more sites I visit through stumbleupon.  I know there was a bug submitted for Lucent about this occurring and there being a patch available at the time however, the ppa that hosted said patch no longer exists and even if it did it presumably wouldn't do much for the xorg package Maverick uses...  The relevant bug was bug#551754 (this being a duplicate but still)

This mostly occurs with noscript enabled but not always, it just seems to really bring the problem to the surface.  On the one hand, I could just disable noscript but that'd unlesh all manner of javascript minions...  On the other...  crashing back to kdm with annoying frequency...

The question I have is: what do I do now?

---

### Post by yuki-nagato on 2010-11-16
bump.

Xorg has been reconfigured although this did not solve the problem which seems to happen every hour give or take pretty randomly.

---

