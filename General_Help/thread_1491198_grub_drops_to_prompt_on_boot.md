---
title: "grub drops to prompt on boot"
date: 2010-05-23
forum: General Help
---

### Post by felixnine on 2010-05-23
lucid
kernel 2.6.32-22 (x64)
grub 0.97-29ubuntu60

this started happening as soon as i installed lucid. when my laptop boots, instead of the grub menu, i just get a prompt. i can solve the problem by doing

```
configfile /boot/grub/grub.cfg
```

and it'll work the first time, most of the time. when it doesn't, i use tab-complete to try to find grub.cfg, and i get something like this

```
/boot/grub/grub.cfg???
```

the trailing characters aren't always '?', sometimes they are just random ascii garbage.

if i run the first command enough times, it'll eventually work, but why is this happening?

i've followed the instructions here a few times. once in a while it'll boot properly, but 90% of the time it doesn't.

---

