---
title: "Removing a half-installed kernel?"
date: 2009-09-04
forum: General Help
---

### Post by hockeyc on 2009-09-04
Hi folks, thanks in advance for your help.

I decided to try my hand at installing a new kernel today to see if some issues with the AX.25 kernel module had been fixed. I followed the instructions here:
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html)

The compile and building into a package seemed to go just fine. When I installed the package it gave me an error about post-install scripts not running correctly and failed.

dpkg and apt-get won't let me purge it, nor can they fix the install. dpkg --list gives me a status of 'iF' for the package (which I also don't understand and can't decipher the list header to tell)

Any ideas?

Thanks again!

---

### Post by hockeyc on 2009-09-05
Figured out it was the nvidia-common scripts which were failing with the new kernel. Removed that package and apt-get automatically finished the failed installation. That kernel still didn't boot, but the one built with the updated instructions at the link below did work.

[http://www.howtoforge.com/kernel_compilation_debian_etch](http://www.howtoforge.com/kernel_compilation_debian_etch)

Hopefully this might help someone :)

---

