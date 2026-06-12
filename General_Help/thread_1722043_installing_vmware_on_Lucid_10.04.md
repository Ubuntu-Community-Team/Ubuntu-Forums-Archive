---
title: "installing vmware on Lucid 10.04"
date: 2011-04-05
forum: General Help
---

### Post by donofrij on 2011-04-05
I downloaded VMware Player 2.5.5-328052.i386.bundle from the VMware site, moved it to my home directory (/home/user) and then in Terminal proceeded to untar the file with "tar=xzvf VMware-player-2.5.5-328052.i386.bundle. I get the following error:

tar: VMware-player-2.5.5-328052-i386.bundle: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2

What am I doing wrong, and how can I successfully unbundle this file so I can proceed to install VMware. By the way, in the man chmod file, there does not appear to be an 'x' option anymore. Is that true?

---

### Post by Mark Phelps on 2011-04-05
The command is incorrect.  Replace the "=" with " -" (a space and a dash).

---

