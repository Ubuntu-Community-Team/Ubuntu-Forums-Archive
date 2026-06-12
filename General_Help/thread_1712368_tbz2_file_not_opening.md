---
title: "tbz2 file not opening?"
date: 2011-03-22
forum: General Help
---

### Post by ibootindos on 2011-03-22
I downloaded the crystalHD linux driver for the broadcom accelerator chip for my HP mini, cause I'm fly like that, and its in a tbz2 file, but whenever I try to extract the file so I can build the driver, I get this error.

bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now

any ideas? Thanks

---

### Post by cynfewl on 2011-03-22
That file, despite its extension, is actually just a tar file.

Try expanding it with 'tar xvf <filename.tbz2>'.

Just a warning too, the crystalHD driver was causing freezes after login on my installation of Maverick.

Alas the performance is well short of Windows even when you get everything working.

---

