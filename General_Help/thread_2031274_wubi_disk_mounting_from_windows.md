---
title: "wubi disk mounting from windows"
date: 2012-07-21
forum: General Help
---

### Post by icegood on 2012-07-21
Why there is no subj at all???
Explore2FS and others don't work, so why developers hasn't create appropriate reader/writer?
Writer under root account for example.

---

### Post by Frogs Hair on 2012-07-21
Wubi installs Ubuntu in a folder inside the Windows partition referred to as the root disk but it is a folder. Windows system information will only display an unknown operating system.

It's possible to access windows in Ubuntu from file system > host ( Wubi only) but not the other way around.

---

### Post by icegood on 2012-07-21
> **Frogs Hair said:**
> Wubi installs Ubuntu in a folder inside the Windows partition referred to as the root disk but it is a folder. Windows system information will only display an unknown operating system.

It's possible to access windows in Ubuntu from file system > host ( Wubi only) but not the other way around.
I understand those obvious things. But should be partition information inside 
.disk file itself. So, where can i read about packing of this file and how to extract it? If it isn't done today doesn't mean it couldn't be done at all! Just share this information in appropriate form right to developers of extract2fs, or users still will load under root command line in recovery mode , manually mount windows partitions, do what they should do, restart under windows to share those things in forum like there. In case when normal boot doesn't work because of stupid compiz fail or so. 
----
P.S. After stupid compiz error i removed f..ng ubuntu at all so i'm out of this game!

---

