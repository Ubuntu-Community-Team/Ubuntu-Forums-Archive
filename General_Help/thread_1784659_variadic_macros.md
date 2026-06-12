---
title: "variadic macros"
date: 2011-06-17
forum: General Help
---

### Post by Alan5 on 2011-06-17
Hi

I am hoping to use the ellipsis in macros with gcc compiling C code. Wikipedia says its OK, but I get failure.

My hope is to provide an interface between code for stdio.h and ncurses. For instance I desire :

```
#define fprintf( A , ... ) ( A == stdout ? printw ( ... ) else fprintf ( A , ... ) )
```For testing I write this :

```
/*    variadic.c
      test variadic macros        */

#include <stdio.h>

#define show( ... ) printf ( ... )

int main ( )
{ show( "%d  HARROW %s\n" , 1 , "WEALD" ) ; return 0 ; }
```The response is :

> variadic.c:9: error: expected expression before ‘...’ tokenThanks for your interest, I would appreciate any advice.

---

### Post by regala on 2011-06-17
> **Alan5 said:**
> Hi

I am hoping to use the ellipsis in macros with gcc compiling C code. Wikipedia says its OK, but I get failure.

My hope is to provide an interface between code for stdio.h and ncurses. For instance I desire :

```
#define fprintf( A , ... ) ( A == stdout ? printw ( ... ) else fprintf ( A , ... ) )
```For testing I write this :

```
/*    variadic.c
      test variadic macros        */

#include <stdio.h>

#define show( ... ) printf ( ... )

int main ( )
{ show( "%d  HARROW %s\n" , 1 , "WEALD" ) ; return 0 ; }
```The response is :

Thanks for your interest, I would appreciate any advice.


usually, GCC is more right than Wikipedia about GCC. [http://gcc.gnu.org/onlinedocs/gcc-4.3.2//cpp/Variadic-Macros.html](http://gcc.gnu.org/onlinedocs/gcc-4.3.2//cpp/Variadic-Macros.html)

try this:
```
#define my_fprintf( A , ... ) ( if (A == stdout) printw ( __VA_ARGS__ ) else fprintf ( A , __VA_ARGS__  ) )
```

by the way you mixed the cond ? foo : bar and the if (cond) then foo; else bar; , so even if you got the correct syntax for variadic macros, you were quite far from it :)

oh and I think that overloading symbols with macros is quite ill-advised...

br,

Mathieu

---

### Post by Alan5 on 2011-06-17
Brilliant, many thanks Mathieu.

__VA_ARGS__ works perfectly with the little test.

And many thanks for the link to the gcc documentation. I have spent days hunting for the answer using Google and never found this primary resource.

Alan

---

