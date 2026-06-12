---
title: "New Packages"
date: 2009-11-12
forum: General Help
---

### Post by Tramx on 2009-11-12
Hi, just a quick question. I'm still using Ubuntu Hardy and I usually install packages for the specific distribution. I was wondering whether it is safe to install packages from newer distributions ie. Karmic, or will this cause installed applications to crash or function improperly? Good to know...

---

### Post by karlson on 2009-11-12
> **Tramx said:**
> Hi, just a quick question. I'm still using Ubuntu Hardy and I usually install packages for the specific distribution. I was wondering whether it is safe to install packages from newer distributions ie. Karmic, or will this cause installed applications to crash or function improperly? Good to know...

Anything can happen.  The shared libraries installed from another system may be incompatible, may have dependencies on other shared libraries or programs at specific versions, etc.

You can try installing packages from newer distributions onto the older ones (if it will work), but you may get your system unusable.

A better way would be to check whether the features you want have been back ported to Hardy since it's an LTS distribution.

---

### Post by Shazaam on 2009-11-12
Adding newer Ubuntu version repositories/apps CAN cause breakage and may result in an unwanted dist-upgrade (ie. Hardy upgraded completely to a newer version). A safe bet would be enabling the "Backports" repo in Synaptic. That way you may get a newer version of an application. Adding the "Proposed" repo to a stable installation is not recommended.

---

### Post by winotree on 2009-11-12
> Adding the "Proposed" repo to a stable installation is not recommended.I'm still learning computers and Linux [and always hope to be learning].  I'd appreciate a bit more information on what you've just said -- not that I've done it but because I've thought of doing it.  What would be the harm?  :???:

---

### Post by Tramx on 2009-11-12
Am I to understand that in Linux, a specific package is made for a certain distro? Hmm, interesting, I think it makes sense though. That's why Ubuntu developers release a new distro around every 6 month because new applications are continuously developed and old libraries are needed to be upgraded.

---

### Post by Shazaam on 2009-11-13
> **winotree said:**
> I'm still learning computers and Linux [and always hope to be learning].  I'd appreciate a bit more information on what you've just said -- not that I've done it but because I've thought of doing it.  What would be the harm?  :???:

If you are confident that you can fix any glitches that can happen go ahead and enable the "Proposed" repository. What I would do is install Ubuntu (any version) as a virtual machine and try different things. If it goes south no harm done to a stable install. My favorite way to tweak/trash operating systems. :)
Just remember, most virtualization apps use their own hard-coded drivers so the vm won't be the same as a regular install.

---

### Post by winotree on 2009-11-13
Well -- that changed my mind for me, didn't it.  :D  Thanks for a direct and candid answer.  I appreciate it.  Really.  ;)

---

