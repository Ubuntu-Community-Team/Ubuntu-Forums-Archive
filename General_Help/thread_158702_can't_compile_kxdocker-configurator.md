---
title: "can't compile kxdocker-configurator"
date: 2006-04-11
forum: General Help
---

### Post by vavoem on 2006-04-11
./configure gives me the following output

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

can anyone help me?

---

### Post by trotski on 2006-04-11
You probably need the xlibs-dev package

---

### Post by vavoem on 2006-04-12
Thanks for your reply
I installed the x-windows-dev package and now it continues up till the point it says i need qt3 i found out i need kde4lib-dev for that.
but when i try to install kde4lib-dev i get in to serious packaging problems.

it will not install a few packages wich are candidate
because it gets into trouble with alsade0 
I 've tried to see what happens if i remove alsade0 but when i do it will remove more or less KDE completely. And offcourse i'm not to keen about that.

---

