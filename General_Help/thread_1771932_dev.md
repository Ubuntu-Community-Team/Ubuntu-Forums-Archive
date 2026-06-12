---
title: "/dev"
date: 2011-05-30
forum: General Help
---

### Post by stribor40 on 2011-05-30
Some of files inside /dev are yellow color and when i try to open it such as "vim something" i get bunch of weird characters. Are device files actually  human readable?

---

### Post by prshah on 2011-05-31
> **stribor40 said:**
> Some of files inside /dev are yellow color and when i try to open it such as "vim something" i get bunch of weird characters. Are device files actually  human readable?

Nope. Most files in "/dev" are virtual files, that are representative of the hardware in your computer. Eg, /dev/sr0 refers to your optical drive, /dev/sda to your hard drive, etc.

Typically, you cannot "read" such files unless the underlying hardware is trying to send some information. (Eg, an ir receiver reporting ir codes).

---

