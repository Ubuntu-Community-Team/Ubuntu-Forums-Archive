---
title: "Need to restore Ubuntu to default"
date: 2010-03-07
forum: General Help
---

### Post by dakoellis on 2010-03-07
long story short, I deleted some files that I should not have, and now I need to restore the computer to default settings.
  I tried using sudo dpkg-reconfigure -phigh -a but I got:

> dpkg-trigger: dpkg-trigger must be called from a maintainer script (or with a --by-package option)


I also tried using the installation CD, but I could not find a way to keep my partitions, like I have done in the past, because the CD is not mounting the partitions on my hard drive.  am i missing something?

Thanks

---

### Post by Arkitekt on 2010-03-07
Do you know which files you deleted?

does 'sudo apt-get install -f' fix anything?

---

### Post by dakoellis on 2010-03-07
> **Arkitekt said:**
> Do you know which files you deleted?

does 'sudo apt-get install -f' fix anything?

I have no idea which files were deleted, and that line does not help.

---

### Post by dakoellis on 2010-03-07
apparently I broke my kernel, should have checked that before posting.  thanks for the reply

---

