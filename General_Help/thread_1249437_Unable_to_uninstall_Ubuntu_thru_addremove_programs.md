---
title: "Unable to uninstall Ubuntu thru add/remove programs"
date: 2009-08-25
forum: General Help
---

### Post by Shane Little on 2009-08-25
I installed Ubuntu on my buddy's PC, trying to turn him to the Linux side but he didnt catch on. Oh well. I installed it inside of windows which partitioned the boot drive. He said when he goes to add/remove programs and selects Ubuntu to remove it tells him that he hasn't the priveledges to do it and prompts him for a command line code to remove. I suggested 'SUDO apt-get remove ubuntu', saw it on here someplace, it didn't recognize the command. Any suggestions from the Gurus? Thanks a bunch. By the way, this isn't the newest release of Ubuntu 9.02 I believe it is. It's actually the one before the newest release.

Shane

---

### Post by uylug on 2009-08-25
If you've installed Ubuntu via Wubi, then boot Windows and uninstall "Ubuntu". It shows up as if it was a normal program. If it does not work, then remove the boot entry by right clicking on My Computer and there is a tab where you can configure the boot screen. Remove Ubuntu or set windows as default and timeout to zero.

You can then free space by removing the ubuntu folder manually.

---

### Post by Shane Little on 2009-08-25
I actually didnt think to have him uninstall by deleting the actual file. Thanks for the reply, lol.

---

