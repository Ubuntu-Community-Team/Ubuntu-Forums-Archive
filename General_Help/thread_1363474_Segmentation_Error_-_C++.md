---
title: "Segmentation Error - C++"
date: 2009-12-24
forum: General Help
---

### Post by one.byte on 2009-12-24
Hi guys!
My first time here, so be gentle.
I don't have much experince on forums (almost zero), so, sorry in advance for any mistake that I might make.

I have a small problem in C++ under Linux. Here's the code: 
```
#include <iostream>
#include <stdlib.h>

using namespace std;

typedef struct node
	  {
          int val;
          struct node *next;
	  }LIST;

LIST *insert(LIST *L, int val) // inserts val at the end of the list;
{
    LIST *nod = new LIST();
    LIST *p;
    p = L;

    nod->val = val;
    nod->next = NULL;

    while (p != NULL)
        p = p->next;
    p->next = nod;
    return L;
}

int main()
{
    LIST *list;
    LIST *q;
    int i;

    for (i=1; i<=10; i++)
        list=insert(list, i);
    q=list;
    while (q != NULL) // prints the list
    {
        cout<<q->val<<" ";
        q = q->next;
    }
    return 0;
}

```

When I try to build&run, I get "Segmentation Fault".
For 6 days I've tried to make this work, but with no success and I can't find the problem/solution. It's getting me crazy. 
Some help will be very, very appreciated.
[Sorry for my English]

It's ok now. I have found the solution. In the code above I did not checked if the list is vid in the first place. 
That was all. Bye bye

---

