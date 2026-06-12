---
title: "Wine-like compatibility layer for MaxOSX programs?"
date: 2006-04-07
forum: General Help
---

### Post by sander marechal on 2006-04-07
Hello,

Does there exist a compatibility layer to run MacOSX programs on Linux, similar to what Wine does for Win32 applications? I've looked around but didn't find anything. My gut feeling says it should't be too hard to do (in comparison to Wine) since Darwin runs on x86 hardware and is based on *BSD.

Thanks in advance!

---

### Post by hw-tph on 2006-04-07
There is no such software for x86 Linux. Macintosh computers run on an entirely different hardware architecture - the powerpc (except from the new Intel Macs and very old Motorola M68K-based Macs) so you would need to use an emulator. Fortunately a good one exists - [PearPC](http://pearpc.sourceforge.net/). Don't expect speed since this is a true emulator, unlike Wine which is an implementation of the Win32 API and associated API's.

Darwin runs on x86 hardware if compiled for it. Similarily, Intel Macs run OSX compiled for x86.


Håkan

---

### Post by trent dillman on 2006-04-07
Since there's the new Intel Macs, hopefully someone starts working on one!

---

