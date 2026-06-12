---
title: "Ubuntu Froze - Caps Lock Blinking"
date: 2010-05-05
forum: General Help
---

### Post by jschille on 2010-05-05
So, I've read the forums and noticed that people experienced this problem in 8.10 and that it seems to be a kernel issue, but found nothing related 10.04.

Ubuntu has NEVER froze on me and just today my computer locked up with the caps lock flashing.

Has this happened to anyone else with 10.04?  What is the fix for this IF ANY!?

Thank you for the help!

---

### Post by CharlesA on 2010-05-05
What kind of keyboard is it? PS/2 or USB?

---

### Post by jschille on 2010-05-05
> **CharlesA said:**
> What kind of keyboard is it? PS/2 or USB?

Im on a laptop.
Dell Studio

---

### Post by CharlesA on 2010-05-05
> **jschille said:**
> Im on a laptop.
Dell Studio

Did anything change, and are there any error messages?

---

### Post by sandyd on 2010-05-05
welcome to the world of kernel panics.

---

### Post by 3rdalbum on 2010-05-05
1. Run Memtest86+ from the GRUB menu. Run it overnight. If it finds errors, then your RAM is starting to fail.

2. Try removing any binary drivers from your system (like the Nvidia or ATI drivers, if you have them) and see if the problem occurs again.

---

