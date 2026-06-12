---
title: "RAID5-Setup / RAID5-REBUILD"
date: 2011-07-23
forum: General Help
---

### Post by cbanakis on 2011-07-23
Seems like it should be a simple question, but maybe not.

I googled everything, but seem to be finding conflicting results.

I have a software RAID5 setup with the following hardware.

HighPoint RocketRaid2314
4 External 5 Bay Sata Enclosures
20 1.5TB 7200RPM Seagate Barracudas.

I have had everything setup and working for quite a while.

Today the dreaded happened, and a drive failed.
No big deal, I have spares on standby.

But when I went to rebuild, I noticed the option...

Cache Policy - Write Back, Or Write Through?

So, I'm wondering, is one better than the other?
Or maybe one might be better during the long rebuilding process, and the other for general use?

Any input will be appreciated.

Thanks

Ubuntu Rocks!

---

### Post by Habitual on 2011-07-23
```
mdadm --detail /dev/md0
```

should tell you the current settings for the raid setup.

I don't know what's "better" but I tend to stick with defaults myself. :)

---

### Post by cbanakis on 2011-07-23
well, its all done with the rebuild, and all is well.

But still not sure if I should be using write back, or write through?

I guess its been working fine this long using Write Back.  But Write Through might be better or worse.

---

### Post by cbanakis on 2011-07-23
I also prefer to stick to defaults.

The only thing here, is that I doubt that the manufacturer had a 30TB RAID Array in mind when they created the defaults.

So Write Back may be best for most people, but when things get a little excessive like mine, Write Through may be ideal.

> **Habitual said:**
> ```
mdadm --detail /dev/md0
```should tell you the current settings for the raid setup.

I don't know what's "better" but I tend to stick with defaults myself. :)

---

### Post by Habitual on 2011-07-23
> **cbanakis said:**
> well, its all done with the rebuild, and all is well.

But still not sure if I should be using write back, or write through?

I guess its been working fine this long using Write Back.  But Write Through might be better or worse.

Glad it all worked out. :)

---

