---
title: "how do i install a bzip2 file?"
date: 2010-10-31
forum: General Help
---

### Post by coreyscx on 2010-10-31
im just wondering and i cant figure it out, thanks guys

---

### Post by Enigmapond on 2010-10-31
bzip2 is just an archive file....what exactly are you trying to install??

---

### Post by sgosnell on 2010-10-31
It's just like a .zip file in Windows.  Use the archive manager to extract it to the directory of your choice, then do whatever needs to be done for the installation.  Read the docs for the package, or whatever it is.  Often the package has to be compiled, and all you get in the archive is source code.  For that, you need to install build-essential, to get the compiler, make, and everything else.  After you have build-essential installed, in the directory where you extracted the files, run './configure', then 'make', then 'sudo make install'.  That's the most common way it works, but you really need to read the docs for complete installation instructions.  bzip2 is just a compressed archive, and could contain any type files at all, just as a .zip file in Windows can.

---

### Post by oldos2er on 2010-10-31
> **coreyscx said:**
> im just wondering and i cant figure it out, thanks guys

Depends on what's in it.

---

