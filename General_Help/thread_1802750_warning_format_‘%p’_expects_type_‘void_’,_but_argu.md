---
title: "warning: format ‘%p’ expects type ‘void *’, but argument 2 has type ‘int’"
date: 2011-07-12
forum: General Help
---

### Post by prateekarya71 on 2011-07-12
/* i wrote the following code to print value of i using *(&i)
/*it gave the  [SIZE=2]**warning: format ‘%p’ expects type ‘void *’, but argument 2 has type ‘int’**[/SIZE]

#include<stdio.h>
void main()
{
int i;
scanf("%d",&i);
printf("value of i by *(&i) = %p",*(&i));

}
plz help

---

### Post by mali2297 on 2011-07-12
> **prateekarya71 said:**
> /* i wrote the following code to print value of i using *(&i)
/*it gave the  [SIZE=2]**warning: format ‘%p’ expects type ‘void *’, but argument 2 has type ‘int’**[/SIZE]

#include<stdio.h>
void main()
{
int i;
scanf("%d",&i);
printf("value of i by *(&i) = %p",*(&i));

}
plz help

*(&i) is synonymous to i and is thus an integer. In printf, use %d instead of %p.

---

