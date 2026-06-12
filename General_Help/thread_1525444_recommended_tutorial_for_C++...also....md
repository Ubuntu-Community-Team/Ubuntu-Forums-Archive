---
title: "recommended tutorial for C++...also..."
date: 2010-07-06
forum: General Help
---

### Post by d3v1150m471c on 2010-07-06
Can someone recommend a good c++ tutorial? I'm not a n00b but i'd prefer something that is directed toward people who have absolutely no experience with coding. Also...wtf

```

// my first program in C++

#include <iostream>

using namespace std;

int main ()
{
  cout << "Hello World!" << endl;
  return 0;
}

```i landed that off some website and gcc will not compile it.  i named the file with a cpp extension, i tried .c as well.... it's mildly annoying

```

/tmp/cchOWd7S.o: In function `main':
hello.cpp:(.text+0x14): undefined reference to `std::cout'
hello.cpp:(.text+0x19): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/cchOWd7S.o: In function `__static_initialization_and_destruction_0(int, int)':
hello.cpp:(.text+0x41): undefined reference to `std::ios_base::Init::Init()'
hello.cpp:(.text+0x46): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cchOWd7S.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

...?

---

### Post by d3v1150m471c on 2010-07-06
apparently i needed to use 
```

g++ -o hello hello.cpp

```

it compiled with no errors.

also... [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

that tutorial is right-on for anyone who is interested.

---

