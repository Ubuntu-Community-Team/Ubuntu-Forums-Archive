---
title: "Nici64 issues ???"
date: 2009-11-23
forum: General Help
---

### Post by NeatO7364 on 2009-11-23
Hi all,

I'm not exactly sure how, but I've managed to screw up a package called nici64. I was attempting to install Novell eDirectory for Linux and I saw a file called this in a few places, but I never used it.

Now whenever I try to install new software, it fails with an error related to nici64. Is there any way to reinstall it?

Here is the detailed error I received when I tried to install the Restricted Drivers:

ldconfig deferred processing now taking place
Errors were encountered while processing:
 nici64
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nici64 (2.7.6-1.01) ...
Initializing NICI ... failed, error -1497
dpkg: error processing nici64 (--configure):
 subprocess installed post-installation script returned error exit status 39
Errors were encountered while processing:
 nici64

---

### Post by NeatO7364 on 2009-11-23
FIXED.

Sorry for posting. Previously after I installed eDirectory the nici64 package didn't show up in Synaptic for some reason. I restarted Synaptic, found the broken package & was able to reinstall without issue. Sorry about that again!

---

