---
title: "Error in Intel C++ Compiler : could not open source alogrithm"
date: 2009-07-04
forum: General Help
---

### Post by ManishSR on 2009-07-04
I am trying my hand on C++ in ubuntu with Intel Compiler 11.
when i tried to compile my project then the error comes out stating
 catastrophic error: could not open source file "alogrithm"
  #include <alogrithm>
                      ^
Plz Help i dont know where i am wrong.
And i still dont know about whether i have c++ standard library or not ?
Thank U in ADVANCE.

---

### Post by TeoBigusGeekus on 2009-07-04
Perhaps
#include **<algorithm>**

---

### Post by ManishSR on 2009-07-04
Thank U [TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094") . It worked.

---

