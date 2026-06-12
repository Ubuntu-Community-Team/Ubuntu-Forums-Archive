---
title: "Bug in srand?"
date: 2009-10-03
forum: General Help
---

### Post by mozza314 on 2009-10-03
I get the same sequence of random numbers when using srand(0) and srand(1), is this supposed to happen? Surely I am not the first to notice this.

```
#include <iostream>
#include <cstdlib>
using namespace std;

int main()
{
    srand(0);
    cout << rand() << endl;
    cout << rand() << endl << endl;
    
    srand(1);
    cout << rand() << endl;
    cout << rand() << endl;
    
    return 0;
}
```gives me:

```
1804289383
846930886

1804289383
846930886
```I'm using ubuntu 9.04.

---

### Post by Brandon Williams on 2009-10-03
It's not a bug; it's intentional that the seed isn't allowed to be 0. I'm not sure why the code converts a seed of 0 into 1, and I'm not sure why the manpage doesn't mention it, but the behavior you see is expected.

---

