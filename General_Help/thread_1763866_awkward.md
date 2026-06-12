---
title: "awkward"
date: 2011-05-20
forum: General Help
---

### Post by blackmail on 2011-05-20
First of all i can't post to the development area of the forum!

Second:

let's say i have the following example:

```
#include <iostream>

using namespace std;

int main(int argc, char **argv) {
	int a;
	int b;
	
	cout<<a+b<<endl;
	return 0;
}
```

The code is not important the important part is that i can't seem to be able to use the eclipse development IDE since it always prompts me to make the friggin main to return an int.

Well i tried adding a return 0; to the end but it did not help, i tried simple main, and nothing i tried int main without the arguments and still nothing i tries void main (...yes i know the new rules...) and still nohting. QT and eclipse are making my life miserable, but now i need eclipse... any ideas please?

the actual code that i need compiles without any problem in G++ and also this example gives the same error in eclipse.
I did not install eclipse i just downloaded it from the site, is that a problem since that's how i saw people using it without any issues. Thank you in advance for your help.

---

### Post by blackmail on 2011-06-17
For people who will have the same problem, don't forget to save your project before every compile, because otherwise things will go haywire...

---

### Post by Zero2Nine on 2011-06-17
Eclipse is an environment for multiple languages right? Maybe it is not set to C++ ?

---

### Post by blackmail on 2011-06-19
Well i have downloaded the CDT version so i think it is set to C++ and mainly nothing else... or so i assume, but i am not used to IDEs, the company where i am hoping to get hired requests it :/

---

### Post by blackmail on 2011-06-19
Anyway as i posted above, the problem was that I didn't save before compiling and so i have received errors... after i realized that eclipse doesn't automatically perform saving operations before compiling stuff started to work...
:popcorn:

---

