---
title: "64-bit binary optimization"
date: 2010-03-19
forum: General Help
---

### Post by nbtrap on 2010-03-19
I recently read somewhere that a binary compiled on a 64-bit machine will be optimized on ANY 64-bit machine, as opposed to a 32-bit machine, which will generally only compile a binary into a form optimized for that machine. Is this true?

---

### Post by nbtrap on 2010-03-19
Bump.

---

### Post by falconindy on 2010-03-19
32-bit is an amorphous term when it comes to x86 architecture. i386, i486, i586, and i686 are all 32-bit but use slightly different instruction sets.

In the same way, 64-bit processors employ slightly different instruction sets, but there's no defined standards as there is for 32-bit. For example, the Core i7 implements the SSE4.2 standard which contains some instructions that a Core2Duo would not, because it only implements SSE4.1. They're both declared amd64 architecture, though.

There was a recent issue with building chromium on AMD processors where SSE had to be disabled in the compilation because AMD's SSE2 equivalent (SIMD) wasn't supporting a machine instruction that gcc was generating and caused the compile to fail. Still, these processors are declared amd64 architecture.

---

