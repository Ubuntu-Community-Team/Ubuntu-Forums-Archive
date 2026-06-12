---
title: "Can't find glib-config, need to install older version of libglib?"
date: 2011-12-13
forum: General Help
---

### Post by Bioinfoswede on 2011-12-13
Am trying to compile Genewise, a sequence comparison program (bioinformatics) that needs glib. I have installed a number of libglib2.0 libraries, including libglib2.0-dev.

The compilation ends with an error message, saying it can't find the file "glib-config" (/bin/sh: glib-config: not found). Some searching around on the net makes it clear that this file only is included in earlier versions of libglib, libglib1.2dev to be more precise. However, I just can't figure out how to install an older package like this. It is not available through Synaptic Package Manager, and I can't find it using apt-get either. Guess they are using the same repositories.

How should I proceed? I would prefer using Synaptic or apt-get rather than just downloading and compiling it myself as I am afraid I might miss some dependencies. Is it possible to add repositories with older releases, and if so, what are they called?

Any help would be much appreciated!

---

