---
title: "Howto fix Flash on Ubuntu 9.10"
date: 2009-12-07
forum: General Help
---

### Post by TDK800 on 2009-12-07
If you are not able to click on flash (e.g. on Youtube), here is how to fix this known bug (works for both 32-bit and 64-bit):

1. Press ALT+F2 and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

2. Add the following line before the last line in the file:
export GDK_NATIVE_WINDOWS=1

3. Save and restart Firefox, or if this doesn't fix it, try restarting Ubuntu.

---

