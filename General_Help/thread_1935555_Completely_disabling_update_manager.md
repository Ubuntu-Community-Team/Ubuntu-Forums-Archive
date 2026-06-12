---
title: "Completely disabling update manager?"
date: 2012-03-04
forum: General Help
---

### Post by Christian Knudsen on 2012-03-04
I'm on Ubuntu 10.04 64-bit and would like to completely disable the update manager. I've unchecked the "Check for updates" box in the settings, but the update manager still pops up once in awhile informing me that there's a new version of GIMP available (I don't want to update). Why does the update manager still check for updates when I'm telling it not to?

---

### Post by apochry on 2012-03-04
Normally it should not notify you anymore.
You can try to uncheck the Update Manager from the start up applications, so it does'n start when you boot the OS.
Another thing you can do is  uncheck the GIMP software source  in the Update Manager under Settings -> Other Software, if you have added the repo manually.


Regards,
Christo

---

### Post by Christian Knudsen on 2012-03-04
Good ideas. Don't know why I didn't think of that. Thanks!:D

---

### Post by MG&amp;TL on 2012-03-04
For me, I remove update manager entirely, but that's me. Probably not recommended.  :evil:

---

### Post by Sonsum on 2012-03-04
> **MG&TL said:**
> For me, I remove update manager entirely, but that's me. Probably not recommended.  :evil:

Wouldn't that remove the ubuntu-desktop metapackage?

---

### Post by wildmanne39 on 2012-03-04
Hi, if you do decide to remove update manager don't forget to run updates manually so you can get security updates.
Thanks

---

### Post by MG&amp;TL on 2012-03-05
> **Sonsum said:**
> Wouldn't that remove the ubuntu-desktop metapackage?


Yes. Is that a problem? It's a metapackage. It's only there so you can install "ubuntu-desktop", rather than $(apt-cache depends ubuntu-desktop). :)

---

### Post by Sonsum on 2012-03-05
> **MG&TL said:**
> Yes. Is that a problem? It's a metapackage. It's only there so you can install "ubuntu-desktop", rather than $(apt-cache depends ubuntu-desktop). :)

I suppose it's not a problem if you manually check for dependencies. Otherwise, the upgrade to Precise might be missing programs (I think).

---

### Post by MG&amp;TL on 2012-03-05
> **Sonsum said:**
> I suppose it's not a problem if you manually check for dependencies. Otherwise, the upgrade to Precise might be missing programs (I think).

Yes. But IMHO, "upgrading" to precise without new installation media is a bad idea, so...yeah, not a problem for me.

I see your point though. However, precise should have ubuntu-desktop as a dependency anyway, so it should get reinstalled.

---

