---
title: "Dynamic Allocation in C"
date: 2011-11-13
forum: General Help
---

### Post by arpanm on 2011-11-13
```
#include <stdio.h>

int
main()
{
        int n;
        scanf("%d",&n);
        int a[n];
        for(int i=0;i<n;i++)a[i]=i;
        for(int i=0;i<n;i++)printf("%d\t",a[i]);
        printf("\n");
        return 0;
}

```
I am wondering why this  program works. I am reading n at run time, so memory is being allocated to a[] at run time without malloc(). How?

---

### Post by davetv on 2011-11-13
Because the scope of "a[]" is local, as I understand it the memory for the array will be allocated on the stack - not the heap, so it doesn't require memory allocation and subsequent deallocation. The stack pointer will return to the top of the stack at the end of the function.

---

### Post by Sazhen86 on 2011-11-13
Variable length arrays were added to C in C99.  Previously the size had to be a constant expression determined at compile time.  

davetv is correct that GCC allocates memory for such arrays on the stack.

Interestingly this addition also changed the way sizeof() works from compile time to runtime.

---

### Post by arpanm on 2011-11-13
> **Sazhen86 said:**
> Variable length arrays were added to C in C99.  Previously the size had to be a constant expression determined at compile time.  

davetv is correct that GCC allocates memory for such arrays on the stack.

Interestingly this addition also changed the way sizeof() works from compile time to runtime.
But, one thing is clear that this allocation is dynamic allocation ? And this is the dynamic allocation without malloc(). So, there re ways to achieve dynamic allocation in C without malloc, right?

---

### Post by Sazhen86 on 2011-11-13
It is dynamic allocation in that is allocated at runtime.  However, unlike malloc(), the memory is allocated on the stack, not the heap, so the usual caveats apply.  C has no way of reporting errors if stack overflow occurs and the standard specifies this situation as undefined behaviour (standard language for a crash if you're lucky and several hours debugging if you're not).

---

