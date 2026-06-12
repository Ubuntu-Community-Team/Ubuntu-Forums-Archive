---
title: "Installing GMP Library"
date: 2011-10-16
forum: General Help
---

### Post by mahaju on 2011-10-16
I think I have installed the GNU Multiple Prercision Library but when I try to compile it it's not working
When I give this command
```
gcc -o test test.c -lgmp
```I get this
```
test.c:3:17: fatal error: gmp.h: No such file or directory
compilation terminated.

```where test.c contains the GMP sample code from Wikipedia

[http://en.wikipedia.org/wiki/GNU_Multi-Precision_Library#Example](http://en.wikipedia.org/wiki/GNU_Multi-Precision_Library#Example)

```
#include <stdio.h> 
#include <stdlib.h> 
#include <gmp.h>   
int main(void) 
{  
mpz_t x;  
mpz_t y; 
 mpz_t result;  
  mpz_init(x); 
 mpz_init(y); 
 mpz_init(result);
    mpz_set_str(x, "7612058254738945", 10);
  mpz_set_str(y, "9263591128439081", 10); 
   mpz_mul(result, x, y); 
 gmp_printf("\n    %Zd\n*\n    %Zd\n--------------------\n%Zd\n\n", x, y, result); 
 return EXIT_SUCCESS; 
}

```I am using lubuntu on VMWare
Please give me some ideas
Or is it that GMP has not been installed properly?
How do I check it

---

