---
title: "Jaunty Qt4 updates killed Skype"
date: 2009-11-11
forum: General Help
---

### Post by whollycow on 2009-11-11
Yesterday I installed some Qt4 updates on my Jaunty machine.  I booted up this morning and tried to start Skype and it dies with the following error:
```
skype: error while loading shared libraries: /usr/lib/libQtGui.so.4: unexpected PLT reloc type 0x03
```
Has anyone else experienced this?  How can I fix this?

---

### Post by squaregoldfish on 2009-11-11
I'm using the latest beta version (2.1.0.47), and everything seems fine here. If you're using the previous version, try upgrading. The beta's rock solid for me, and the extra features are nice anyway!

Steve.

---

### Post by whollycow on 2009-11-11
Thanks.  I'm already running the beta.  I even tried uninstalling and reinstalling the package but that didn't fix it.

---

### Post by whollycow on 2009-11-11
I fixed the problem by reinstalling all Qt4 packages.  Something must have gone wrong during the update.

---

