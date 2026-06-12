---
title: "C++ double to string"
date: 2010-11-12
forum: General Help
---

### Post by J V on 2010-11-12
I've seen stringstream, printf() variants, etc... Is there no way to simply print an integer or double with cout or save as string?

[code\]cout << intordouble; // Doesn't work
string s = (string) intordouble;
cout << s; // Also doesn't work...[/code]

---

### Post by bryangwilliam on 2010-11-12
Yes, you should be able to just send the int or double to cout...
```

int main()
{
        double num = 12.997;
        cout << num << endl;
        return 0;
}

```

This prints out "12.997" to my console. Am I not understanding you correctly?

---

### Post by J V on 2010-11-12
```
#include <iostream>
using namespace std;

double f(int x,int y){
return 2.0;
}

int main(){
double d = f(3,2);
cout << d;
return 0;
}

```> undefined reference to `std::cout'

Edit: Ok, I've slimmed it down to this and I'm still getting errors:
```
#include <iostream>
using namespace std;
int main(){
cout << 2.0 << endl;
return 0;
}
```I must be compiling wrong...

```
~/test/c++$ gcc helloworld.cpp 
/tmp/ccFJde3T.o: In function `main':
helloworld.cpp:(.text+0xd): undefined reference to `std::cout'
helloworld.cpp:(.text+0x12): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(double)'
helloworld.cpp:(.text+0x17): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
helloworld.cpp:(.text+0x1f): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccFJde3T.o: In function `__static_initialization_and_destruction_0(int, int)':
helloworld.cpp:(.text+0x4d): undefined reference to `std::ios_base::Init::Init()'
helloworld.cpp:(.text+0x52): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccFJde3T.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

---

### Post by bryangwilliam on 2010-11-12
I have never come across this before... try putting an "endl" or newline at the end out your output string. It worked for me when I added that to your piece of code.

---

### Post by bryangwilliam on 2010-11-12
Try compiling with g++... I've had much more consistent results that way.

---

### Post by Ancanus on 2010-11-12
gcc does not link to C++ libraries, therefore it is unable to find std::out.

Either compile with g++ as *bryangwilliam* suggested, or include a flag with gcc to point to the C++ libraries.

---

### Post by J V on 2010-11-12
Oh man, can't believe that, I thought gcc was the c++ compiler and something else was the C compiler... sorry about that /facepalm

---

