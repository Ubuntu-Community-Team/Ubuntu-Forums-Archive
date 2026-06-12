---
title: "Error running a script"
date: 2011-09-27
forum: General Help
---

### Post by Mazate on 2011-09-27
Hola... I'm trying to execute an .sh file.  When I do so, I get the following error:

./Indexing_unix_3_9_9.sh: 346: bin/unpack200: not found
Error unpacking jar files. The architecture or bitness (32/64)
of the bundled JVM might not match your machine.

The funny thing is that I just did it yesterday without any issues but I ended up reinstalling Ubuntu.  When to do it again and I got the above error.  Anyone have any ideas?

---

### Post by seawolf167 on 2011-09-27
When you reinstalled Ubuntu did you reinstall with the 32bit (x86) or 64bit (x86_64) architecture? What was your systems' architecture before the reinstall? Looks like there is probably a version mismatch.

Can you post the contents of the script inside [noparse]```

```[/noparse] tags so we can see what it is trying to do.

---

