---
title: "Disappearing memory"
date: 2012-08-28
forum: General Help
---

### Post by jgcsd on 2012-08-28
I have 4GB of RAM in my computer. But Ubuntu and the BIOS screen itself reports it as 3.25GB exactly.

I found a BIOS option called "memory hole remapping", which when enabled causes BIOS to see 4GB and Ubuntu to also see 4GB also.

However, with this on, there are many error messages in "dmesg", and graphics reverts to gallium on the llvm pipe, software rendering.

Also, liveCDs refuse to boot with this on.

Does anybody have any idea what's going on?

---

### Post by SlugSlug on 2012-08-28
your on board graphics is using your system RAM.

Leave it as is or buy a graphics card

---

### Post by jgcsd on 2012-08-29
No it isn't. I use a graphics card.

---

### Post by SlugSlug on 2012-08-30
Do you have a 64-bit CPU?

[http://en.wikipedia.org/wiki/PCI_hole](http://en.wikipedia.org/wiki/PCI_hole)

---

