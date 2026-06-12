---
title: "What happens when apt-get install linux?"
date: 2011-03-24
forum: General Help
---

### Post by qwerty1234 on 2011-03-24
Hi,

first of all sorry for my newb quiestion :)

I ran "sudo apt-get install linux" by a mistake on my Ubuntu 10.10, and suddenly got these installed:

```
(...)
Setting up linux-image-generic (2.6.35.28.36) ...
Setting up linux-generic (2.6.35.28.36) ...
Setting up linux-image (2.6.35.28.36) ...
Setting up linux (2.6.35.28.36) ...
```

Did I do anything stupid, or did I just update to latest kernel? :confused:

---

### Post by mendhak on 2011-03-24
I don't think it's stupid, since what you've done happens anyway when there's a kernel update.  linux-image, for example, is the binary image of the kernel, followed by the version number.  If you reboot your machine, are you given several options in your Grub menu?

---

