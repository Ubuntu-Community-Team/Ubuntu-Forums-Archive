---
title: "Kernel compilation DSDT error"
date: 2010-11-21
forum: General Help
---

### Post by mErchamion on 2010-11-21
Hello everybody! Due to some ACPI issues in my toshiba laptop, I am trying to recompile 2.6.32 kernel in Ubuntu 10.04. I have disasembled the DSDT table and commented the lines for the _OSI declarations, as you can find in the attached DSDT table. I can compile it using:
iasl -tc DSDT.dsl
Then, I attach the custom DSDT.aml table using the make xconfig command in the kernel source directory.  As a result, I get the errors you can also find attached. 

I am just getting involved in DSDT reading, and I would appreciate if any of you can give me a hand on it. In this issue, some system specific patches for this problem are available, but none of them work on my toshiba L500-ST5507

---

### Post by mErchamion on 2010-11-28
Hello! 
Anybody answered my question, but I found an alternate solution. I was not able to recompile the DSDT in order to include the custom one in the Kernell compilation. Anyway, following the directions here:
[http://homeport.org/~bcordes/satellite-l500-install.html]("http://homeport.org/%7Ebcordes/satellite-l500-install.html")

I was able to apply the proper patch to the latest Kernel. My laptop is working flawlessly with my first fully functional self-compiled kernel. 

Thankyou all.

---

