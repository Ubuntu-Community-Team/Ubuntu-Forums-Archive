---
title: "Removing software that wasnt installed thorugh synaptic"
date: 2010-03-03
forum: General Help
---

### Post by ricardino on 2010-03-03
Hi all,

I installed a piece of software without using synaptic (netbeans 6.8 ). I now want to know how i go about uninstalling that software?

Any help would be appreciated.
Thanks

---

### Post by Bradj47 on 2010-03-03
> **ricardino said:**
> Hi all,

I installed a piece of software without using synaptic (netbeans 6.8 ). I now want to know how i go about uninstalling that software?

Any help would be appreciated.
Thanks

If you installed it using a .deb package, **sudo apt-get remove** should work. If you manually installed it into a single directory, running **rm -r** on that directory should take care of it.

---

