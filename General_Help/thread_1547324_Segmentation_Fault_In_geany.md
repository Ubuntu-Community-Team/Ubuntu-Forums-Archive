---
title: "Segmentation Fault In geany"
date: 2010-08-06
forum: General Help
---

### Post by Asad_S on 2010-08-06
Hello fellows,
I just made a pretty simple program in geany (GCC with default options)
and I ended up with Segmentation fault.

here's the program

#include <stdio.h>
int main(void)
{
    int n,l,u,m,arr[7]={5,10,15,20,25,30,35};
    printf("Enter search element");
    scanf("%d", &n);
    l=0;u=6;
    while(l!=u)
    {
        
        if(n==arr[m])
        {
            printf("The element found at %d", m+1);
            break;
        }
        if(n<arr[m])
            u=m-1;
        if(n>arr[m])
            l=m+1;
        m=(l+u)/2;
        
    }
    
    return 0;
}


program is pretty simple and it performs binary search on an array.

I know what segfault is but here I m clue less about why it is happening.

and one thing more, the program runs fine in turbo C++ compiler.

Same thing happened earlier too when I was making a program which included some simple string manipulation.


Any help is appreciated.



________________________________________________

Ok friends!
I figured it out.
Thanks anyways!

---

### Post by dv3500ea on 2010-08-06
This should be in the Programming Talk forum.
Also, please use [CODE] blocks to make your program easier to read.
Read [this wikipedia article]("http://en.wikipedia.org/wiki/Segmentation_fault") on why segmentation faults may occur.
It's probably to do with the arrays you have used - make sure you only access arr[0] - arr[6].

---

