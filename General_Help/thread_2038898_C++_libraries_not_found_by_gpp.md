---
title: "C++ libraries not found by gpp"
date: 2012-08-07
forum: General Help
---

### Post by guiltySparks on 2012-08-07
Hi all,

I recently decided to learn C++. However, when I try to compile the familiar "Hello, world!" program on 12.04, I keep running into a peculiar issue.

Here's my program:

```
#include <iostream>
using namespace std;

int main() {
	stdout::cout << "\nHello, World!\n\n";

	return 0;
}
```

And when I compile it, I receive the error message:

```
$ gpp helloWorld.cpp
helloWorld.cpp:2: error: Requested include file not found
```

Does anyone have any idea what's going on here? I've already installed the build-essential package, so I'm at a bit of a loss as to why the compiler is complaining.

Thanks in advance!

---

### Post by MG&amp;TL on 2012-08-07
I have no idea what *gpp* is, but shouldn't that be *g++*?

---

### Post by guiltySparks on 2012-08-07
> **MG&TL said:**
> I have no idea what *gpp* is, but shouldn't that be *g++*?

Wow, you're completely right.

If only I had posted here first before spending a few hours trolling google. :)

---

### Post by steeldriver on 2012-08-07
gpp is a pre-processor I think?

To compile, you'd want something like

```
g++ -o myprog myprog.cpp
```BTW I think your cout line should be 

```
cout << "\nHello, World!\n\n";
```or (more C++ like)

```
cout << endl << "Hello, World!" << endl << endl;
```It doesn't need any qualifier since you have a 'using namespace std' directive - if you omit the 'using' directive then the correct form would be

```
std::cout << std::endl << "Hello, World!" << std::endl << std::endl;
```

---

