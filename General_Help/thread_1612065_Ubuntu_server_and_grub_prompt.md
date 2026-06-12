---
title: "Ubuntu server and grub prompt"
date: 2010-11-02
forum: General Help
---

### Post by miguelastico on 2010-11-02
I searched that, and I didn't find any solution in the million posts that are around...

I have a machine that we use as file server, one 2TB hard drive, and a raid5 with 5.5TB.
The 2TB is /dev/sdb while the raid is /dev/sda

We tried CentOS and everything works fine. We are trying to install ubuntu server 64bit, and so far we had no luck.

The installation works fine, however grub stops at the prompt without any menu.
I tried a lot of solutions on line, and nothing works, grub simply doesn't see any drive. 
I tried to install grub on sdb, but still no luck.

What can I do?

---

### Post by miguelastico on 2010-11-05
really? nobody there?

As an update, I can tell that doing:

```
root(hd0,0)
makeactive
chainloader +1
boot
```

boots the correct hard drive
how can I make it happen at boot time?

---

