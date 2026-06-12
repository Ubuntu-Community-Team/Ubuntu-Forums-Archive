---
title: "Install a shadow system?"
date: 2011-09-26
forum: General Help
---

### Post by AlexBooton on 2011-09-26
Hi,

I'm wondering if this is possible.

I'd like to set up a 2nd Ubuntu system that would sit next to the existing one and maintain a complete shadow of the first.

I'm not talking about mirroring drives but rather mirroring an entire system.  

The second system would, ideally, get updates of any changes made to the first including configuration changes and software updates and additions or deletions.  IOW, everything.

The idea is to have an immediate replacement in case the first system fails.

Manually switching ethernet cables would be OK, but I'd like everything else to be automatic.

If necessary, I can envision some sort of daily update of the second system by copying the drives on the first.  But again, I'd like this to be automatic.

Is this possible or just a pipe dream?

Thanks

---

### Post by Diametric on 2011-09-26
Not entirely sure, but my first thoughts on the subject are it sounds like there is specific software needed to pull this off, if possible at all.  Second, if you're shadowing system "a" to system "b", anything other than hardware failure will be replicated to system "b".  So, if there is some sort of failure on system "a", system "b" is sure to have it has well....

Good luck.

---

### Post by bodhi.zazen on 2011-09-26
Sounds to me as if you simply need a back up strategy.

I suggest you back up your home directory, or any other data you have as well as any system files you manually configure / customize.

There really is no need for a "shadow system" as you call it, any system files you might need are in the repositories.

---

### Post by WorMzy on 2011-09-26
It should be relatively easy to set something like this up using rsync and cron; but I expect it would suck up cpu cycles like a champion.

I recommend that you follow bodhi.zazen's suggestion and just backup your home folder (as well as any website stuff you have in /var/www, and any seriously modified config files from /etc). Everything else is easily replaceable.

---

