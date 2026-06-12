---
title: "whats wrong with this program?"
date: 2010-02-02
forum: General Help
---

### Post by luposolo on 2010-02-02
// dem01-1.cpp
// John C++ Molluzzo

#include <iostream>

using namespace std;

int main()
{  // This is the body of the
      function main()
cout << "This our first C++ program." << endl;
cout << "It works!! << endl;

return 0;
}

---

### Post by lloyd_b on 2010-02-02
> **luposolo said:**
> // dem01-1.cpp
// John C++ Molluzzo

#include <iostream>

using namespace std;

int main()
{  // This is the body of the
      function main()
cout << "This our first C++ program." << endl;
cout << "It works!! << endl;

return 0;
}

Could you please tell us why you think something's wrong with it?  I don't see any problems with the actual code, so if you could provide the errors that you're getting on compile/run it might provide a clue.

One possibility - are you compiling with "gcc" or "g++"?  Compiling the code with "gcc" will generate compiler errors - you need to use the "g++" command for C++ code.

Also, in the future I'd suggest posting such questions to the Programming section, rather than General Help - you're more likely to get a good answer to programming questions there.

Lloyd B.

---

### Post by gmargo on 2010-02-03
You are missing the closing double-quote on the "It works!!" line.  If you use a programming-oriented editor with syntax highlighting, it would be easier to see.  Or you could look at the output from the compiler which clearly states 'error: missing terminating " character'


```

// dem01-1.cpp
// John C++ Molluzzo

#include <iostream>

using namespace std;

int main()
{ // This is the body of the function main()
    cout << "This our first C++ program." << endl;
    cout << "It works!!" << endl;
    return 0;
}


```

---

