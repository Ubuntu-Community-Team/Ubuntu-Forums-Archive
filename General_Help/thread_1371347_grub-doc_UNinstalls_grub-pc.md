---
title: "grub-doc UNinstalls grub-pc?"
date: 2010-01-03
forum: General Help
---

### Post by jf/ on 2010-01-03
I'm just slightly confused here, but... what the? Why does installing grub-doc remove BOTH grub-pc, and grub-common?

So basically it seems like by installing grub-doc, I have uninstalled grub totally (yes, it is still there as the bootloader, but i have no way of updating it now!) from my system.

What's the conflict between grub-doc and grub-pc, such that grub-pc has to be removed?

---

### Post by Leppie on 2010-01-03
> **jf/ said:**
> I'm just slightly confused here, but... what the? Why does installing grub-doc remove BOTH grub-pc, and grub-common?

So basically it seems like by installing grub-doc, I have uninstalled grub totally (yes, it is still there as the bootloader, but i have no way of updating it now!) from my system.

What's the conflict between grub-doc and grub-pc, such that grub-pc has to be removed?
grub-doc is the documentation for grub legacy. grub-pc and grub-common are the two packages of grub2.
there is a bug reported for this: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/493968](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/493968)

uninstall grub-doc and re-install grub2.

---

### Post by jf/ on 2010-01-03
> **Leppie said:**
> grub-doc is the documentation for grub legacy. grub-pc and grub-common are the two packages of grub2.
there is a bug reported for this: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/493968](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/493968)

uninstall grub-doc and re-install grub2.

right! got it, thanks. I assume you mean reinstall grub-pc ? (in my case)

---

### Post by jf/ on 2010-01-03
> **jf/ said:**
> right! got it, thanks. I assume you mean reinstall grub-pc ? (in my case)

nvm, no need to answer that thanks.

---

### Post by Leppie on 2010-01-03
you can choose to either install grub2 (dummy package) or grub-common and grub-pc. both methods will have the same result.

---

### Post by jf/ on 2010-01-03
right. Thanks for the clarification!

---

