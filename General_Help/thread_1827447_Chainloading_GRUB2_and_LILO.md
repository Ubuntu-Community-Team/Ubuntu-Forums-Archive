---
title: "Chainloading GRUB2 and LILO"
date: 2011-08-18
forum: General Help
---

### Post by tb75252 on 2011-08-18
I am running Ubuntu 11.04, 32-bit.  I now want to install, on a separate partition, Slackware 13.37 (which uses the LILO boot manager).  I will install LILO in the root partition of Slackware and need to find a way to chaiload to LILO from GRUB2.
How do I do that?

---

### Post by dandnsmith on 2011-08-18
Slackware may be configured to set up LILO, but that doesn't mean you have to use it.
If you're currently set up with Grub2 and want to add the Slackware, do the install but don't let it install LILO. Then run grub-update (or is it update-grub?) which will rescan your system and add entries for any OSs it finds.
HTH

---

