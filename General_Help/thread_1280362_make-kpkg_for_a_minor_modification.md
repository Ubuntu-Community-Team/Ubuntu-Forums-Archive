---
title: "make-kpkg for a minor modification"
date: 2009-10-01
forum: General Help
---

### Post by ddreamer on 2009-10-01
I tried to compile a new kernel with tuxonice incorporated. On my previous compilation, the lzo option was modular, and it failed. This time, I have included lzo by using make menuconfig. To recompile, I typed: 
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

but no new .deb file was generated.
I don't want to "make-kpkg clean" and recompile again for such a minor modification.
Any way to work around?

---

### Post by ddreamer on 2009-10-13
Anybody helps me?

---

