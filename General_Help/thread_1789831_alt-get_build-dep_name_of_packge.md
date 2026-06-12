---
title: "alt-get build-dep name of packge"
date: 2011-06-24
forum: General Help
---

### Post by lex1 on 2011-06-24
When you build depenancis with apt=get for any package you are going to install from source which directory do the depenacies go into?

And I build the package from for example /home/lex1 will those dependancies be found
In this case the only command I need to run (which is not normal) is 
./Install

lex1;)

---

### Post by oldos2er on 2011-06-24
They are installed in the system in the same manner as any other package (dpkg -L <packagename> will show you exactly). Compiling source code in your home folder will find the dependencies just file.

---

