---
title: "C++ not working"
date: 2010-12-05
forum: General Help
---

### Post by mindlessbrain on 2010-12-05
Hello all,

I am trying to get a c++ program running. When I realized it was doing absolutely nothing I tried out a simple hello world program, still nothing.

```

#include <iostream>

using namespace std;

int main ()
{
    std::cout<<"Hello, World!\n";

    return 0;
}

```

jill@jill-desktop:~$ cd /home/jill/Desktop
jill@jill-desktop:~/Desktop$ g++ test.cpp
jill@jill-desktop:~/Desktop$ 

Nothing.

I already uninstalled/reinstalled g++. Any tips?

---

### Post by GregBrannon on 2010-12-05
You're not getting an error message, so something's happening - or at least DID happen the first time you ran it.  The g++ command compiles the source into object files.  Check the directory.

---

### Post by Random_Dude on 2010-12-05
> **mindlessbrain said:**
> 
```

#include <iostream>

using namespace std;

int main ()
{
    std::cout<<"Hello, World!\n";

    return 0;
}

```

Are you getting any error message?
I'm not sure if it is the problem, but you don't need to write std::cout<<"Hello, World!\n";, you can do it like this:

```

#include <iostream>

using namespace std;

int main ()
{
    cout<<"Hello, World!\n";

    return 0;
}

```

Cheers :cool:

---

### Post by bouncingwilf on 2010-12-05
Er.... You may have successfully compiled it with the g++ test.cpp command but to run it you should now try typing

./a.out 

to get the program to compile to an executable called test; g++ -o test test .cpp
and execute as ./test

bouncingwilf

---

