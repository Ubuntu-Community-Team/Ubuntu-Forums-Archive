---
title: "How do you remove kernels from a previous install, that don't show up in synaptic"
date: 2012-01-21
forum: General Help
---

### Post by someitalian123 on 2012-01-21
I installed a copy of ubuntu on top of a previous install and I still see my old kernels in grub but I don't see them in synaptic or the ubuntu software center. How can I get rid of the kernels from the old install without using the package manager?

---

### Post by kazztan0325 on 2012-01-21
I usually use 'Ubuntu Tweak' to remove older kernels.

Please refer this web page to add its PPA to Software Source.
"Ubuntu Tweak Stable PPA"
[https://launchpad.net/~tualatrix/+archive/ppa]("https://launchpad.net/~tualatrix/+archive/ppa")

---

### Post by dcstar on 2012-01-21
> **someitalian123 said:**
> I installed a copy of ubuntu on top of a previous install and I still see my old kernels in grub but I don't see them in synaptic or the ubuntu software center. How can I get rid of the kernels from the old install without using the package manager?

Delete them from the /boot folder, then:
```
sudo update-grub
```

---

### Post by claracc on 2012-01-21
I think you can find this guide [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462) useful to delete or hide older kernels in different ways.

---

### Post by someitalian123 on 2012-01-21
> **kazztan0325 said:**
> I usually use 'Ubuntu Tweak' to remove older kernels.

Please refer this web page to add its PPA to Software Source.
"Ubuntu Tweak Stable PPA"
[https://launchpad.net/~tualatrix/+archive/ppa]("https://launchpad.net/%7Etualatrix/+archive/ppa")

Ubuntu Tweak can only get rid of kernels that are recognized by the package manager

> **dcstar said:**
> Delete them from the /boot folder, then:
```
sudo update-grub
```

That did the job, thank you.

---

