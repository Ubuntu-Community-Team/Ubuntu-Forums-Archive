---
title: "Where is Adobe Acrobat Now on 10.10?"
date: 2010-10-11
forum: General Help
---

### Post by nutznboltz on 2010-10-11
Where has the Adobe Acrobat (A.K.A acroread) been hidden?

It was in the parters repository on Lucid.

Before that you could get it from Medibuntu.

Now I can't find it on 10.10.

Please tell me if you know where to look for it.

Thanks

---

### Post by M4570D0N on 2010-10-11
> **nutznboltz said:**
> Where has the Adobe Acrobat (A.K.A acroread) been hidden?

It was in the parters repository on Lucid.

Before that you could get it from Medibuntu.

Now I can't find it on 10.10.

Please tell me if you know where to look for it.

Thanks
If you open Synaptic and go to origin, it should be under:

maverick/main (archive.canonical.com)

Check your software sources (go to the other sources tab) to verify that you have Canonical Partners checked.

alternatively, you can go to etc/apt/sources.list and verify that you have
```
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner
```
uncommented.

---

### Post by nutznboltz on 2010-10-11
Oh, in the past activating the Partners repository by using the Software Sources GUI would cause "apt-get update" to run when you closed the GUI.

Now it doesn't so until I ran "apt-get update" acroread didn't show up.

---

