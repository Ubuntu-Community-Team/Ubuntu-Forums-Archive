---
title: "Mounting Reiser4"
date: 2006-06-20
forum: General Help
---

### Post by Enigmatic on 2006-06-20
Is there a way to easily mount Reiser4 filesystems in Ubuntu? I tried the sudo mount command, but a type of reiser4 was not recognized.

---

### Post by Iandefor on 2006-06-20
Does installing libreiserfs help? ```
sudo aptitude install libreiserfs
``` I'm not at all certain if it will, but it looks like it's what you need.

---

### Post by thasheep on 2006-06-21
You need a kernel built to support reiser4 (reiserfs is reiser 3.x). Look for guides for building kernels but use sources that support reiser4. Official Ubuntu and vanilla kernels (the standard kernel.org kernels) do not support it. See [http://www.namesys.com/install_v4.html#vanilla](http://www.namesys.com/install_v4.html#vanilla) for patches against vanilla. The 2.6.15 ones should also work against linux-sources (in synaptic). Otherwise, try the mm (development) kernel from [http://www.kernel.org](http://www.kernel.org) - it already supports reiser4.
Now make sure you enable (best as module) reiser4 under filesystems.

---

