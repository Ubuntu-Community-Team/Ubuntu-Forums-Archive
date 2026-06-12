---
title: "Install a patch file"
date: 2011-11-04
forum: General Help
---

### Post by newport_j on 2011-11-04
I have a patch file
 
002-fix_load_address_substitution.patch. I would like to install it in the Valgrind source area becuase I believe that it will solve a problem which I am haviing running large files through Valgrind memcheck.
 
My Valgrind install works fine, but it crashes on large memory hungry programs and maybe this will work and fix the problem. I hope so. 
 
What is the syntax? I know about dry-run, backup (-b) and replace to the original (-R). I just cannot get the patch command to change the Valgrind source files so I can at least see if this patch will sove my problem.
 
Newport_j

---

### Post by andrew.46 on 2011-11-04
The syntax for patch is:

```

patch -pnum <patchfile

```

The *-pnum* option will vary according to the structure and location of the patch.

---

