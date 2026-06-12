---
title: "Resume wont...well...resume"
date: 2011-04-23
forum: General Help
---

### Post by briman0094 on 2011-04-23
I was in the middle of an update through Update Manager when something caused it to fail (probably the internet glitching out again). It locked my filesystem into read-only mode and asked me to restart the computer. After restarting, it loaded into grub but instead of listing all of the OSes I have installed, it went straight to the "grub >" command line. I booted into Ubuntu manually using the default commands, and did "sudo update-grub". Everything is working fine except resume. When I hibernate it, it seems to work fine, but now when I try to resume from the image it says it can't read the image and says something about different kernels. What do I need to do to fix it?

---

### Post by Habeouscorpus on 2011-04-23
Well, the different kernel message might be happening because you're booting into a kernel different than the default. Or because some thing's hosed up. Check in Synaptic for broken packages.

---

### Post by briman0094 on 2011-04-24
Got it. It was the broken packages. Thanks!

---

