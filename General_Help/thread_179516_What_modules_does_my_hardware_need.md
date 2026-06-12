---
title: "What modules does my hardware need?"
date: 2006-05-20
forum: General Help
---

### Post by Basu on 2006-05-20
I'm thinking about trying out Arch Linux, but to get a proper install I need to manually set the kernel modules. Can I use Ubuntu to figure out what modules my hardware actually needs and not all the things that are installed? And has anyone used Minix3 here?

---

### Post by empthollow on 2006-05-20
i'm not familiar with Arch Linux, but you can do:
```
lsmod
```
to get a list of kernel modules that your system is using, 
the linux kernel is the same source code no matter the distro, it's just compiled with different options. 

if you want the modules in a text file for easy reference you can:
```
lsmod > name_of_text_file
```

good luck

---

### Post by 5-HT on 2006-05-22
[quote=Basu]I'm thinking about trying out Arch Linux, but to get a proper install I need to manually set the kernel modules. [/quote] 
I've been looking into Arch recently and while I'm by no means knowledgeable on the matter (just getting familiar with Arch by reading the documentation), you shouldn't need to manually select your modules. You should be able to use the auto-detection utility (hwdetect) to find the proper modules for your system. You can, or course, manually select the modules you want to load, but shouldn't need to if you don't want to.

Have you read this: [http://www.archlinux.org/docs/en/guide/install/arch-install-guide.html]("http://www.archlinux.org/docs/en/guide/install/arch-install-guide.html") ?

---

