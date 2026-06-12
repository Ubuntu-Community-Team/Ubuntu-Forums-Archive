---
title: "how to enable CONFIG_MAC80211 ?"
date: 2010-09-10
forum: General Help
---

### Post by TomFumb on 2010-09-10
Hi,

I'm having some real trouble installing compat-wireless and I really hope someone can help me out.  After having lots of trouble with syntax errors in various versions available here: [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/) (I'm still not sure why they aren't identified by versions that do / don't compile) I'm finally moving forward, now I encounter this error

config.mk:57: *** "ERROR: Your >=2.6.27 kernel has CONFIG_MAC80211 disabled, you should have it CONFIG_MAC80211=m if you want to use this thing.".  Stop.

I have tried researching this but all I get from Google is direct links to other versions of the config.mk script which is really unhelpful.

So far I have managed to figure out that this may require re-compiling the kernel on my system.  This is not something I am familiar with at all.  Can anyone suggest how I could get past this issue?

ANY help much appreciated.

---

