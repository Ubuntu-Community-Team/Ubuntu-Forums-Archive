---
title: "g++ internal compiler error on &quot;Hello World!&quot; program"
date: 2012-09-14
forum: General Help
---

### Post by marianoa on 2012-09-14
Hi everybody,

I need some help on this. I'm trying to compile a simple Hello World program
using g++. The program is this 
```

#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}

```I try to compile with
```
g++ filename.cpp
```and I get
```
g++: internal compiler error: Segmentation fault (program as)
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.6/README.Bugs> for instructions.

```Any idea?

---

### Post by marianoa on 2012-09-14
I solved the problem reinstalling binutils

---

### Post by haresear on 2012-09-14
The program code you posted compiles and runs okay here. There must be something amiss with your g++ installation. I would suggest reinstalling the package "g++".

---

### Post by marianoa on 2012-09-14
Hi haresear,

thanks for your help. As you've seen I've found a solution, the problem was created by the gnu portable assembler (as) so I reinstalled binutils and that solved the problem.

---

