---
title: "error while loading shared libraries: libpcsclite.so.1: wrong ELF class: ELFCLASS64"
date: 2011-08-23
forum: General Help
---

### Post by pasha811 on 2011-08-23
Ubuntu 11 04 64bit here.

Trying to install Oracle Virtual Desktop Client. It installs ok with dpkg but at at launchtime I got the following:

**error while loading shared libraries: libpcsclite.so.1: wrong ELF class: ELFCLASS64**

ldd command reports (see attach):

**libpcsclite.so.1 => not found**

I then copied the lib to usr/lib which is known to be scanned by java, with no success.

Is there a way to install the 32bit version of libpcsclite into Ubuntu 64bit?

- Best 
- Pasha811

---

### Post by Keith_Beef on 2011-09-15
Try reading [this thread]("http://ubuntuforums.org/showthread.php?t=1745645&highlight=wrong+ELF+class%3A+ELFCLASS64").

---

