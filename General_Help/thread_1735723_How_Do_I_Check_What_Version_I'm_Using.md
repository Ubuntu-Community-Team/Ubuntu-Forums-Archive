---
title: "How Do I Check What Version I'm Using?"
date: 2011-04-21
forum: General Help
---

### Post by El3mentGamer on 2011-04-21
Simple question i know: but I downloaded the 11.04iso but it says in the shutdown screen that its 10.04... :/

---

### Post by plucky on 2011-04-21
> **El3mentGamer said:**
> Simple question i know: but I downloaded the 11.04iso but it says in the shutdown screen that its 10.04... :/

Open a terminal and ```
lsb_release -a
```

---

### Post by lithopsian on 2011-04-21
The Ubuntu version is not a single defined thing, but rather a whole collection of versions of pieces of software including the Linux kernel.  This is most simply defined by the repositories you are using, which would be Natty for 11.04.  It is perfectly possible to have mostly 11.04 versions of stuff but some 10.04 versions.  Or maybe there is a typo :)

---

### Post by El3mentGamer on 2011-04-21
So, aparently i have 10.10. Is there anyway i can update without restarting my harddrive?

---

### Post by lithopsian on 2011-04-21
lsb_release says Ubuntu 10.10 Maverick?  Did you even install 11.04?

You can upgrade from 10.10 to 11.04 without doing a complete reinstall from the CD, but what is the problem with rebooting?  You're going to have to do it sooner or later whichever way you upgrade.  Personally I wouldn't recommend trying to upgrade until you are very sure you have a good consistent copy of 10.10 and you don't seem at all sure about that.

---

