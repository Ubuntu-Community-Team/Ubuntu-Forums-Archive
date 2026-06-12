---
title: "Adobe Air messes up Google Chrome?"
date: 2009-12-13
forum: General Help
---

### Post by xtjacob on 2009-12-13
I've been using Google Chrome on Ubuntu 9.10 64-Bit, and I recently decided to install Adobe Air. After I finally finished it and tested it it worked, but now when I try to start Chrome I get the error ```
/opt/google/chrome/google-chrome: error while loading shared libraries: libplds4.so.0d: wrong ELF class: ELFCLASS32
``` and it fails to start. I've removed Air, but it still doesn't work. Anyone have an idea whats going on?

---

### Post by Spirit55555 on 2010-01-02
I have the same problem.

Did you follow this install guide: [http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html) ?

---

### Post by xtjacob on 2010-01-02
Yah, I fixed it by uninstalling Air and replacing the files from a computer of the same architecture. The problem was Chrome has 64-bit libraries, and Air used the 32-bit so chrome wouldn't work.

---

### Post by loboes41 on 2010-01-09
I'm having this problem too. Is there a way to fix it, or am I just not able to run both Chrome and Air on a 64 bit system?

---

### Post by xtjacob on 2010-01-09
I think it's safe to say you shouldn't install both of them on a 64-bit computer, until Abode comes out with a true 64-bit version.

---

### Post by Spirit55555 on 2010-02-16
I fixed the problem by re-installing the **libnspr4-0d** package.

---

