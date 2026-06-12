---
title: "Missing files for debugging"
date: 2012-08-04
forum: General Help
---

### Post by squaregoldfish on 2012-08-04
I'm trying to do some debugging, and I appear to be missing some fundamental files:

```
Cannot find file '../sysdeps/unix/syscall-template.S'

```

The usual apt-file search has turned up a blank, and my Google-fu has failed me. Can anyone help?

---

### Post by steeldriver on 2012-08-04
I *think* it's an assembly template file used during the compilation of glibc - it's probably part of the glibc source package?

[http://stackoverflow.com/questions/3546760/how-does-compiler-know-that-the-function-you-used-is-a-system-call](http://stackoverflow.com/questions/3546760/how-does-compiler-know-that-the-function-you-used-is-a-system-call)

---

### Post by squaregoldfish on 2012-08-04
Sounds promising. However, there doesn't appear to be a libc sources package in Precise. Or maybe I'm missing the correct repositories from my apt setup - Synaptic has a '-' instead of a tick for the source packages and I can't change it.

---

