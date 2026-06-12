---
title: "Debian Live Magic"
date: 2010-02-01
forum: General Help
---

### Post by Randymanme on 2010-02-01
Debian Live Magic has been generating my Debian Live System for about 2 hours, now.  How long is it supposed to take?

---

### Post by lykwydchykyn on 2010-02-01
On my dual-core machine at work debian live usually takes around 30 minutes to build a system.  It has to download everything, build the virtual filesystem, install everything, etc.

If you're building it on a P III (as your signature indicates), I can only guess at how long it will take.  How fast is your internet?

---

### Post by Randymanme on 2010-02-01
[QUOTE=How fast is your internet?[/QUOTE]

Don't know, precisely.  It's Roadrunner high speed, though.

---

### Post by lykwydchykyn on 2010-02-01
Well, I've only tried the live wizard once.  The command line equivalents give you pretty verbose status output, so if it seems stuck you can always try the commands and see what the problem is.

I think building a basic image is as simple as:
```

lh_config
lh_build

```

Though you probably want to tweak it more than that.

---

### Post by Randymanme on 2010-02-01
I'm bailing out.  Still, just for future reference, how long should it take?

Thanks.

---

### Post by lykwydchykyn on 2010-02-01
> **Randymanme said:**
> I'm bailing out.  Still, just for future reference, how long should it take?

Thanks.

I can't possibly guess on your hardware.  it's a fairly involved process that's going to vary widely depending on the system specs.

---

