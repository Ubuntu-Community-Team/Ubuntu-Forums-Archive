---
title: "I force-installed a 32bit package (I'm on 64-bit,) how do i uninstall?"
date: 2009-11-24
forum: General Help
---

### Post by sexyclient2 on 2009-11-24
I don't see it in synaptic and google hasn't returned any help.  Anyone know how I can force-uninstall a 32 bit package I force-installed?

The package is zsnes, by the way, and I found a 64 bit version here: 
[http://mirrors.kernel.org/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2.1ubuntu1.1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2.1ubuntu1.1_amd64.deb)

---

### Post by Giblet5 on 2009-11-24
Open a terminal window (Apps -> Accessories -> Terminal)

```
sudo apt-get remove zsnes --purge
```

---

### Post by Darael on 2009-11-24
Try "sudo dpkg -r [packagename]"?

---

### Post by sexyclient2 on 2009-11-24
> **Darael said:**
> Try "sudo dpkg -r [packagename]"?
Worked like a charm.  Thanks.

---

