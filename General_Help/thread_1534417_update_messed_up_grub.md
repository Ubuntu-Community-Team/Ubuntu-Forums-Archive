---
title: "update messed up grub"
date: 2010-07-19
forum: General Help
---

### Post by yobird42 on 2010-07-19
I did a system update and it did something to the grub loader and now all I can select is my windows partition. I'm not really sure how to go about restoring my grub loader. I had ubuntu 10.04.

---

### Post by wojox on 2010-07-19
Reinstall from a [LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by lidex on 2010-07-19
Using grub 2? Probably need to re-install it. Go here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
You'll want the first section: 9.10 and beyond

Just to be sure run this command in a terminal:
```
dpkg -l | grep "grub"
```

If the output is version 1.9x it's grub2 if .xx it's legacy and you'll want the second section.

---

### Post by yobird42 on 2010-07-19
how do I install it if I can't boot into ubuntu? Live CD?

---

### Post by techunit on 2010-07-19
I would first recommend that you make sure it has anything to do with GRUB. It could be that Ubuntu isn't recongnized.. I believe what you can do is boot into a live CD open a terminal and type the following...

```
sudo update-grub
```

---

### Post by lidex on 2010-07-19
> **yobird42 said:**
> how do I install it if I can't boot into ubuntu? Live CD?
Yes. Follow *wojox's* link.

---

