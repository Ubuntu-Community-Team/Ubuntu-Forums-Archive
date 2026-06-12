---
title: "generic and generic-pae"
date: 2010-07-02
forum: General Help
---

### Post by jamesorr on 2010-07-02
I switched to the generic-pae kernal image, which works great, but update now wants to update both generic and generic-pae.

How can I set it up so that it only uses generic-pae? 

If I try to deselect generic in synaptic it just wants to mark it again.

---

### Post by mcduck on 2010-07-02
Everything that is installed will also get updates.

Just uninstall the generic kernel (and it's related files) and you won't see updates for it any more.

Anyway, it sounds like you already tried to do something like that, but how exactly did you try to "deselect" the generic kernel? You need to right-click and select "mark for removal" every generic kernel package, and then click the Apply button to remove those packages.

---

### Post by jamesorr on 2010-07-02
I figured it out, I still had some backport stuff that was referencing generic rather than generic-pae.

---

