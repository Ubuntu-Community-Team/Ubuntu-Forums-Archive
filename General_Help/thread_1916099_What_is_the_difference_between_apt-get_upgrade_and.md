---
title: "What is the difference between apt-get upgrade and apt-get dist-upgrade?"
date: 2012-01-27
forum: General Help
---

### Post by THPubs on 2012-01-27
Some say that dist-upgrade is to upgrade the distribution... Actually, that's not true... Its an old story...

The man pages say that 'upgrade' will update the packages without touching the dependencies and 'dist-upgrade' will also touch the dependencies and remove them if it wants to.

I can't fully understand this... Can some one please make this clear? A full explanation? Is it a risk to use dist-upgrade? Why do we have two commands like this?

Thanks in advance...

---

### Post by snowpine on 2012-01-27
"apt-get upgrade" will never add/remove any packages from your system. (similar to "aptitude safe-upgrade")

"apt-get dist-upgrade" will add/remove packages if necessary. (similar to "aptitude full-upgrade")

Example: an updated kernel is available. "dist-upgrade" will give you the new kernel; "upgrade" will not.

I personally use only "dist-upgrade." It is the command-line equivalent of what the GUI Update Manager does.

---

