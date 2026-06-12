---
title: "What causes a kernel panic?"
date: 2009-10-13
forum: General Help
---

### Post by Roasted on 2009-10-13
I'm trying to figure out what's wrong with a problematic computer a co-worker gave to me to fix up.

The symptoms are this:

1 - Windows XP CD fails to copy files when installing, yet the CD is perfectly clean.
2 - All 3 versions of Ubuntu LiveCD's I've tried freeze when loading the LiveCD image.
3 - When booting to GParted LiveCD, it prompts me with a kernel panic.

I've reseated the memory, unplugged the hard drive and tried to reboot to GParted, I also tried a different CD-Rom drive. No luck on anything.

With the computer acting weird like this, but having nothing to go on besides the kernel panic GParted gave me, where do I go with it? What causes a kernel panic?

---

### Post by skillllllz on 2009-10-13
Sounds like bad RAM. Try running the memory test from the boot menu of the Ubuntu Live CD. Let it run for a few hours to test it thoroughly.

---

### Post by Roasted on 2009-10-13
> **skillllllz said:**
> Sounds like bad RAM. Try running the memory test from the boot menu of the Ubuntu Live CD. Let it run for a few hours to test it thoroughly.

Bingo.

I took 1 stick out and all of the sudden GParted boots just fine. Thanks!

---

### Post by skillllllz on 2009-10-14
Awesome, glad you figured it out. :-)

Please be sure to mark this thread as solved.

---

