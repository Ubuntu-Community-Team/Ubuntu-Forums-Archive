---
title: "g++ problem"
date: 2010-08-22
forum: General Help
---

### Post by cyber2791 on 2010-08-22
Hi , i have ubuntu 10.04. I've installed gcc and g++, but if i use g++ test.cpp it says that:
test.cpp:1:21: error:  iostream : No such file or directory
test.cpp:2:21: error:  fstream  : No such file or directory
test.cpp: In function ‘int main()’:
test.cpp:8: error: ‘cin’ was not declared in this scope
test.cpp:9: error: ‘ofstream’ was not declared in this scope
test.cpp:9: error: expected ‘;’ before ‘g’
test.cpp:10: error: ‘g’ was not declared in this scope

This is my source
```

#include< iostream >
#include< fstream  >
using namespace std;
int main()
{

    int a,b;
    cin>>a>>b;
    ofstream g("sum.out");
    g<<a+b;

    return 0;
}

```I have all the libraries in /usr/include/c++/4.4.
I don't know what to do to get it work.

---

### Post by surfer on 2010-08-22
try this:

```

#include <iostream>
#include <fstream>

using namespace std;
int main()
{

    int a,b;
    cin>>a>>b;
    ofstream g("sum.out");
    g<<a+b;

    return 0;
}

```

---

### Post by jpaugh64 on 2010-08-22
Also try adding ".h" to the ends of those included files. I know that this is required for gcc; I don't know if that's true for g++.

---

### Post by cyber2791 on 2010-08-22
> **surfer said:**
> try this:

```

#include <iostream>
#include <fstream>

using namespace std;
int main()
{

    int a,b;
    cin>>a>>b;
    ofstream g("sum.out");
    g<<a+b;

    return 0;
}

```

Ah, thanks man :p. I really didn't saw that. Thanks Again !!!!!

---

