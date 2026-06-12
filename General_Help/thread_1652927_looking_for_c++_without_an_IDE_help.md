---
title: "looking for c++ without an IDE help"
date: 2010-12-25
forum: General Help
---

### Post by drswingingblades on 2010-12-25
New to linux, I use mostly c++ at school so I need to get this working.

I have g++ compiler installed

I made a hello world program just to see how this works

```
#include <iostream>
using namespace std;

void main{

cout << "test";

}
```
but i get this error. do i need to install another library and where do i get it?

```
test.cpp:4: error: variable or field &#8216;main&#8217; declared void
test.cpp:4: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x

```I realize i could just "int main" but that isnt how i code so id like to get this resolved

thank you

---

### Post by lykwydchykyn on 2010-12-25
I'm no expert on c++, but my understanding has always been that main() is *supposed to* return an int, at least on Unix or Unix-like systems.  This int becomes the exit status of the program after it closes (so it should return zero unless there was an error).

There may be a compiler flag to override this, but why would you deviate from the standard which the compiler and OS expect?

---

### Post by A_M_S on 2010-12-25
Try this code:

```


#include <iostream>
using namespace std;

main(int argc, char* argv[]){

cout << "test";

}


```

---

### Post by drswingingblades on 2010-12-25
> **A_M_S said:**
> Try this code:

```


#include <iostream>
using namespace std;

main(int argc, char* argv[]){

cout << "test";

}


```


yeah this works... am I gonna have to run a windows compilers through wine to not initialize main like this?

everything that gets graded at school has be either be int main or void main

---

### Post by emagmant3 on 2010-12-26
> **drswingingblades said:**
> New to linux, I use mostly c++ at school so I need to get this working.

I have g++ compiler installed

I made a hello world program just to see how this works

```
#include <iostream>
using namespace std;

void main{

cout << "test";

}
```
but i get this error. do i need to install another library and where do i get it?

```
test.cpp:4: error: variable or field ‘main’ declared void
test.cpp:4: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x

```I realize i could just "int main" but that isnt how i code so id like to get this resolved

thank you

Using void main is not standard c++. the reason is outlined here [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044841143&id=1043284376](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044841143&id=1043284376)

The standard says any program must return weather or not it was successful. returning 0 means success and other values can be used for your own purposes.

---

