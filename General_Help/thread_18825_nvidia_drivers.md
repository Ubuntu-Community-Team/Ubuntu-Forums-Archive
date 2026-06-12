---
title: "nvidia drivers"
date: 2005-03-08
forum: General Help
---

### Post by sysrq on 2005-03-08
I have been looking around for about two days for a solution to this problem. I run the nvidia installer and it all goes well till it test loads the compiled module, the output from the installer is:
   nvidia: version magic '2.6.10 preempt K7 gcc-3.4' should be '2.6.10 preempt
   K7 gcc-3.3'
I tried removing gcc-3.4 but then the nvidia installer complained that cc didn't exist, is there a way to get either the make process for the kernel to use gcc-3.4 or the nvidia installer to use 3.3 or another fix for this problem?

---

### Post by crane on 2005-03-08
Did you try using apt first or
Are you just wanting to install the newest nvidia drivers? I used apt to install and I have had no problems as of yet.

---

### Post by sysrq on 2005-03-09
Will the prepackaged ones work with a custom kernel? I highly doubt it will.

---

### Post by sysrq on 2005-03-09
Updating the gcc symlink to point to gcc-3.4 then recompiling my kernel, had to do it anyways due to some new patches, and then tried using the nvidia installer and it worked fine.

---

