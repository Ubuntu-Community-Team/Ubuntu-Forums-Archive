---
title: "g++ default header files missing."
date: 2011-10-16
forum: General Help
---

### Post by bharadwaj on 2011-10-16
Hi,

I installed g++ compiler in my Ubuntu and when I am trying to compile this program: ```
//#include <stdio.h>
#include <iostream>

main(){

//puts("HelloWorld");
cout<<"Hello World"<<endl;

}
```

I get the following error in the terminal: 

> sirius@codie:~/workspace/bs$ g++ test.cpp
test.cpp: In function &#8216;int main()&#8217;:
test.cpp:5:1: error: &#8216;cout&#8217; was not declared in this scope
test.cpp:5:22: error: &#8216;endl&#8217; was not declared in this scope


My gcc runs with no problems. I am trying to work in SunStudio and it is not able to resolve the default paths for C++ standard libraries either.

How do I make available these libraries in C++, none of the default ones seem to work. I tried searching online, but with pain, if anybody has ever come across similar problem or know what I am talking about, please help me out.  

Thank you
bharadwaj

---

### Post by TeoBigusGeekus on 2011-10-16
You've forgotten to declare the namespace:
```
#include <iostream>
main(){
using namespace std;
cout<<"Hello World"<<endl;
}
```
or
```
#include <iostream>
main(){
std::cout<<"Hello World"<<std::endl;
}
```

---

