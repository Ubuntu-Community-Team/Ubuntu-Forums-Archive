---
title: "Firefox: java and acrobat plugins don't work after upgrade to Lucid"
date: 2011-01-07
forum: General Help
---

### Post by afilonov on 2011-01-07
I upgraded 2 laptops from Hardy to Lucid. After that, acrobat (8.1.2) and java (6.2) plugins stopped working. Both plugins work OK in Seamonkey. Java plugin also works fine in Chrome.
When starting Firefox from terminal, I'm getting messages:


LoadPlugin: failed to initialize shared library /opt/Adobe/Reader8/Browser/intellinux/nppdf.so [/opt/Adobe/Reader8/Browser/intellinux/nppdf.so: cannot open shared object file: Permission denied]
LoadPlugin: failed to initialize shared library /opt/java/jdk1.6.0_20/jre/lib/i386/libnpjp2.so [/opt/java/jdk1.6.0_20/jre/lib/i386/libnpjp2.so: cannot open shared object file: Permission denied]
2.4+ kernel w/o ELF notes? -- report this
Unknown HZ value! (37) Assume 100.

I have 755 permissions on both files. This happens on both laptops: System76 Gazelle and IBM Thinkpad T41.

Anybody had the same problem?

---

### Post by afilonov on 2011-01-08
Well, problem was solved by installing java plugin and acrobat reader from repositories

---

