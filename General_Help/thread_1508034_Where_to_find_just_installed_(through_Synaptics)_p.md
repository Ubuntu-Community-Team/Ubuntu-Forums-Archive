---
title: "Where to find just installed (through Synaptics) prgms ?"
date: 2010-06-12
forum: General Help
---

### Post by pstein on 2010-06-12
I just installed p7zip-full through Synaptics.
 
Fine. And now?
 
Where do I find the just installed program?
 
Are all programs always installed into the same directory?
 
Peter

---

### Post by dino99 on 2010-06-12
open nautilus and unhide files and folders with ctrl+h

---

### Post by pstein on 2010-06-12
Hmm, and in which directory is 7zip installed?

---

### Post by oldos2er on 2010-06-12
```
dpkg -L p7zip
``` will show you where each file in the package is installed.

---

### Post by llawwehttam on 2010-06-12
7zip in linux is a command line program. However I believer you can use its libs through the archive manager

---

### Post by SeriousName on 2010-06-12
7zip is a command line program. You could use it from the command line ("7z" or "7za"), but in fact the archiving program included in Ubuntu can handle it for you. Just try double-clicking on a 7z file to open it. If you want to compress something to 7zip, right-click it and choose "Compress," and 7zip format should be available in the drop down box.

---

### Post by pstein on 2010-06-13
> **oldos2er said:**
> ```
dpkg -L p7zip
``` will show you where each file in the package is installed.
 
If I type your suggested code I get:
 
"Package 'p7zip' is not installed"
 
Maybe this is because I installed p7zip through Synaptics?
 
Does dpkg recognize synaptics installed prgms?
 
Peter

---

### Post by oldos2er on 2010-06-13
> **pstein said:**
> Does dpkg recognize synaptics installed prgms?

Yes, they're all part of the APT system.

Retry the command with "p7zip-full".

---

