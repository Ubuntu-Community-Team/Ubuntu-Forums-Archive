---
title: "Getting Apps To Share Bandwidth?"
date: 2005-02-27
forum: General Help
---

### Post by JamesV on 2005-02-27
I'm using Hoary with a DSL connection. If I run a Synaptic update and then run Firefox to surf the web while Synaptic is downloading packages, Firefox is unusable because Synaptic is hogging 100% of my DSL bandwidth. Is this a Synaptic problem or is there a system-wide config somewhere to tell all programs to share bandwidth on demand? TIA.

---

### Post by tomchuk on 2005-03-15
What you really need is per-process bandwidth throttling, but I'm not aware of a simple way to do that. You can however limit your uploads and downloads to decrease latency. There's a great script to do just this: wondershaper.
```
sudo apt-get install wondershaper
man wondershaper
zcat /usr/share/doc/wondershaper/README.gz | less
```
That should give you a good idea of what's going on.

---

### Post by francesc on 2005-03-16
You can also try this:

[http://www.ubuntuforums.org/showthread.php?t=20342&highlight=download+limit](http://www.ubuntuforums.org/showthread.php?t=20342&highlight=download+limit)

---

### Post by JamesV on 2005-03-26
[QUOTE=francesc]You can also try this:

[http://www.ubuntuforums.org/showthread.php?t=20342&highlight=download+limit](http://www.ubuntuforums.org/showthread.php?t=20342&highlight=download+limit)[/QUOTE]

This works great. I throttled my Synaptic back and now I can surf while Synaptic downloads packages. I'm a happy camper now. Thanks for the tip.

---

