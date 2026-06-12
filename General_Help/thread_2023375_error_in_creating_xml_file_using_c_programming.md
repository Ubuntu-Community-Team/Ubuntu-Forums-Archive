---
title: "error in creating xml file using c programming"
date: 2012-07-12
forum: General Help
---

### Post by fivestaar on 2012-07-12
I want to create a xml file through a C program. I am using gcc and tinyxml.

```
#include"/usr/include/tinyxml.h"
#define TIXML_USE_STL
//#include<tinyxml.h>

void dump_to_stdout(const char* pFilename);

int main()
{
dump_to_stdout("example1.xml");
return 0;
}

void dump_to_stdout(const char* pFilename)
{
TiXmlDocument doc(pFilename);
bool loadOkay=doc.LoadFile();
if(loadOkay)
{printf("\n%s:\b",pFilename);
}
else
{printf("failed to load file \"%s\"\n",pFilename);
}
}
```[B]
Error generated is: [/B]
divya@ubuntu:~/Desktop/Ccodes$ gcc -c x2.c
In file included from x2.c:1:
/usr/include/tinyxml.h:51: fatal error: string: No such file or directory
compilation terminated.


tinyxml.h header is there on the specified location, yet its saying theres no such file.
What seems to be the problem here?

Any help is appreciated.

---

### Post by steeldriver on 2012-07-12
What build environment do you have? did you install any additional packages (e.g. build-essential)?

> **fivestaar said:**
> 
divya@ubuntu:~/Desktop/Ccodes$ gcc -c x2.c
In file included from x2.c:1:
/usr/include/tinyxml.h:51: **fatal error: string: No such file or directory**
compilation terminated.


tinyxml.h header is there on the specified location, yet its saying theres no such file.
What seems to be the problem here?

Any help is appreciated.

The error appears to be about a file called string (declaring the C++ string class), not about the tinyxml.h file itself. Here is an excerpt from tinyxml.h:

```

#ifdef TIXML_USE_STL
      #include <string>
      #include <iostream>
      #include <sstream>
      #define TIXML_STRING        std::string 
#else
      #include "tinystr.h"
      #define TIXML_STRING        TiXmlString 
#endif
```so you can see if your code #defines TIXML_USE_STL then it wants to include the C++ string / iostream / sstream headers and will fail if you don't have those on your system

**EDIT: you should probably be compiling with g++ not gcc if you are trying to use C++ / STL components**

---

