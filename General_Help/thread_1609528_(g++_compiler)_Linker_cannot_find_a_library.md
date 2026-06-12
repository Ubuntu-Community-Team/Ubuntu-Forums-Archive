---
title: "(g++ compiler) Linker cannot find a library"
date: 2010-10-30
forum: General Help
---

### Post by Taak on 2010-10-30
I need to compile a c++ program **A** using an external library **B**. I have the external library **B** in .o and .a formats.
 
 
When I try to compile the program **A** with the Makefile, the linker gives me this error:
 
/usr/bin/ld: cannot find -libNameB
collect2: ld returned 1 exit status
 
I tried: export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/libNameB_path/
 
But it didn't work.
 
What should I try?

---

### Post by Taak on 2010-10-31
Fixed adding the .a library to the /usr/lib folder.

---

