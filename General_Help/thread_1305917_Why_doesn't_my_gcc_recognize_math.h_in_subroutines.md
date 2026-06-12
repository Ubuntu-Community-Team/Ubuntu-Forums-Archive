---
title: "Why doesn't my gcc recognize math.h in subroutines?"
date: 2009-10-30
forum: General Help
---

### Post by LRico on 2009-10-30
Hello to all of you.
I was trying to develop some little calculus application and gcc is giving me some problems with math.h.
If I try to compile this:

> #include <stdio.h>
#include <math.h>

int main(void) {
 printf("\n exp(1)=%lf", exp(1.0));
}

I find no problems. But if I write down this:
> 
#include <stdio.h>
#include <math.h>

double result(double x);

int main(void) {
 printf("\n exp(1)=%lf", result(1.0));
}
double result(double x) {
 return exp(x);
}

it doesn't work, giving the error " undefined reference to 'exp' ".

Maybe its a noob mistake, but I wonder why this happens.

---

### Post by muteXe on 2009-10-30
I found this link. Hope it's of some use mate:
[http://www.linuxforums.org/forum/linux-programming-scripting/125526-c-gcc-math-h-lm.html](http://www.linuxforums.org/forum/linux-programming-scripting/125526-c-gcc-math-h-lm.html)

EDIT:  in fact try putting 1.0 in your exp function rather than passing in the x variable just as a quick test.  Post #7 looks quite informative.

---

### Post by LRico on 2009-10-30
It was completely true! g++ compiles right, while gcc doesn't look to find some libraries.
Thank you very much for the tip, now I can focus on debugging.

---

