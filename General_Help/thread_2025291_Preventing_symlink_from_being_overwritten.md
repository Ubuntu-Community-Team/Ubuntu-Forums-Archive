---
title: "Preventing symlink from being overwritten?"
date: 2012-07-14
forum: General Help
---

### Post by Kyrio on 2012-07-14
I'm using Opera as my default web browser, and to protect the file where it stores the passwords (wand.dat) I moved it to an encfs encrypted directory and put a symlink in its place.

The problem is, every time I close Opera the symlink gets overwritten with a new copy of wand.dat (I hoped it would work as a redirection to the original file in the encrypted directory).

I also tried to create the symlink as root so that the ownership is root:root (I'm running Opera as a normal user) and yet the file gets overwritten somehow.

Any suggestions would be appreciated. Thanks.

---

