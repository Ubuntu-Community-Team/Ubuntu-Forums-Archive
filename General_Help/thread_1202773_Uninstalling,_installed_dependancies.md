---
title: "Uninstalling, installed dependancies"
date: 2009-07-02
forum: General Help
---

### Post by AnotherMuggle on 2009-07-02
If I install something via the Synaptic Package Manager and it installs a bunch of other things that the package is dependant upon, how do I undo all those changes?

For example, I installed "smartmontools" and at the same time it installed 3 other items.  Is there any way I can find out what those other things were and remove the entire lot?

Cheers in advance,
Tom

---

### Post by oldos2er on 2009-07-02
**sudo apt-get autoremove** will uninstall orphaned dependencies. Also look into the programs debfoster and deborphan.

---

### Post by AnotherMuggle on 2009-07-02
> **oldos2er said:**
> **sudo apt-get autoremove** will uninstall orphaned dependencies. Also look into the programs debfoster and deborphan.

Thanks mate.  Does "orphaned dependencies" mean any dependencies that were installed but are no longer required by anything that's currently installed.

---

### Post by michy99 on 2009-07-02
> **tomkear2006 said:**
> Thanks mate.  Does "orphaned dependencies" mean any dependencies that were installed but are no longer required by anything that's currently installed.

Exactly.

---

### Post by AnotherMuggle on 2009-07-02
> **michy99 said:**
> Exactly.

Brilliant, just what I was after!

I just read the details for debfoster in the Synaptic Package Manager and it sounds like a brilliant tool.  I may give it a go

---

