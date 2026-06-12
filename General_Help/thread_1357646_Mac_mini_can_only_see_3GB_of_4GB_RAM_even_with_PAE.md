---
title: "Mac mini can only see 3GB of 4GB RAM even with PAE Kernel"
date: 2009-12-17
forum: General Help
---

### Post by SlappyPappy on 2009-12-17
I have a Mac mini with Ubuntu 9.10 on it and it only sees 3GB of the 4GB of RAM.

I tried using the PAE kernel to see all of it but it doesn't work.

Any thoughts out there? I was wondering if it was the Mac architecture that was preventing it.

Thanks for any help you can provide.

---

### Post by Darael on 2009-12-17
The only thing I can think of is that some of the RAM might be being allocated as additional graphics memory on the BIOS level, and thus not being presented to the OS - I don't know, since I don't have masses of experience with macs! Nevertheless, you might want to have a poke of any likely-looking BIOS settings - though be careful. If in doubt, ask before experimenting!

---

