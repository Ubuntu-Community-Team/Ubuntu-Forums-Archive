---
title: "Graphics Error"
date: 2011-12-18
forum: General Help
---

### Post by Sorceror71 on 2011-12-18
I've been running Ubuntu 10.04 on a 7 year old laptop for some time now and suddenly when trying to boot up yesterday I received the following error message:  

'Ubuntu is running in low graphics mode. The following error was encountered.  You may need to update your configuration to solve this.  (EE) open/dev/fb0: No such file or directory'

This is actually preventing me from properly booting up the OS to actually do anything.
How can I fix this without reinstalling as I don't want to lose anything saved in my home folders?

---

### Post by 2F4U on 2011-12-18
Could be a hardware problem, for example with the hard disk. Did you look into the system log file? It may contain hints on what the problem is.

---

### Post by sudodus on 2011-12-18
/dev/fb0 refers to framebuffer. Search for that on the internet (or parts of the error output text)!

---

