---
title: "compiling question"
date: 2011-02-18
forum: General Help
---

### Post by nerdy_kid on 2011-02-18
I've been compiling stuff with the usual ccmake . make and make install for a while now, but now I'm starting to compile suites of applications, such as Calligra (Koffice).  Is there any easy way to have the compilation spit out several .debs for the various components?  thanks in advance :)

---

### Post by seawolf167 on 2011-02-18
Unless the various components have their own configure/make/make installs, I do not know how to have it create multiple .debs

I do know that [checkinstall ]("http://www.asic-linux.com.mx/%7Eizto/checkinstall/")is nice to have when compiling from source as it gives you an easy way to remove packages you install (everything is the same up to "make install", instead you just use "make checkinstall"). It may also have a way to split up the components, but I have not read very far into the documentation.

---

