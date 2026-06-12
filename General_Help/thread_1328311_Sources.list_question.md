---
title: "Sources.list question"
date: 2009-11-16
forum: General Help
---

### Post by Uncle Spellbinder on 2009-11-16
In sources.list, both deb and deb-src are uncommented.  I'd read somewhere that unless I was a program writer/coder, deb-src was not needed for the general user. So, is deb-src necessary? Can I delete those entries? Or are they important to the operation of Ubuntu?

Example:
```
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates universe
```

---

### Post by drs305 on 2009-11-16
You generally don't need the src files. If you want to remove them from the sources.list permanently, the easiest way may be to open Synaptic: Settings, Repositories, and untick the "Source code" in "Ubuntu Software" and Source listings in Other Software/Third Party Software. Then Reload.

---

### Post by Uncle Spellbinder on 2009-11-16
> **drs305 said:**
> You generally don't need the src files. If you want to remove them from the sources.list permanently, the easiest way may be to open Synaptic: Settings, Repositories, and untick the "Source code" in "Ubuntu Software" and Source listings in Other Software/Third Party Software. Then Reload.

Or I could just leave them and comment them as such?

```
deb http://archive.ubuntu.com/ubuntu/ karmic universe
##deb-src http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe
##deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates universe
```

Old fashioned, I guess. I prefer terminal > sudo gedit /etc/apt/sources.list

---

### Post by drs305 on 2009-11-16
Yes, same thing. In fact, if you comment all the "src-..." references, apt-get update, and then go into Synaptic, it will have unticked the Sources boxes for you there as well.

---

### Post by Uncle Spellbinder on 2009-11-16
Great. Appreciate the help.

---

