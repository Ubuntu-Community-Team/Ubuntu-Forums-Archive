---
title: "MAKE and Makefile update"
date: 2011-02-24
forum: General Help
---

### Post by anifort on 2011-02-24
Hello guys,
I have a question that confuses me a lot. If i have a makefile which i use to compile, and then i update that depentencies or commands of my make file, do i have to call Make clear or does MAKE realises that since that update date of the makefile is after the date of the builded files, it will automatically rebuild them without the need to call make clear?

Thanks in adnace

---

### Post by 3Miro on 2011-02-24
> **anifort said:**
> Hello guys,
I have a question that confuses me a lot. If i have a makefile which i use to compile, and then i update that depentencies or commands of my make file, do i have to call Make clear or does MAKE realises that since that update date of the makefile is after the date of the builded files, it will automatically rebuild them without the need to call make clear?

Thanks in adnace

Makefile doesn't check if it has been updated. Besides, if you make large changes to your project (like link to different libraries, use different parameters) even those changes affect a small number of files, it is still better to rebuild the entire thing.

Go for make clean.

---

### Post by anifort on 2011-02-25
> **3Miro said:**
> Makefile doesn't check if it has been updated. Besides, if you make large changes to your project (like link to different libraries, use different parameters) even those changes affect a small number of files, it is still better to rebuild the entire thing.

Go for make clean.

thanks! that helps! i had an idea but i dont know if i can do it or if its valid. Can i add the makefile itself as a dependency so that it checks its date anyway?

---

