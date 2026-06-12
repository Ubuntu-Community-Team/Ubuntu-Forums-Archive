---
title: "working with pthreads"
date: 2011-03-06
forum: General Help
---

### Post by flldom001 on 2011-03-06
Hi all, 

when using pthread_create I wish to pass a list to the routine function, and then in the routine (i.e. the new thread) use that very same list, but I dont know how to:

int main....
{
....
/* create parent thread */
pthread_create(&ParentThreadIdentifier, &setOfParentThreadAttributes, routine, (void*) &aList);
....
}

void * routine (void * aparameter) //this routine should be able to return any type
{
... etc
}

essentially I want to use the child thread to create a tree of threads using recursion, my base case is for when the list size ==2.

Thus my second question is, once I have performed the computation at the base case how do i go about sending the data to the parent thread? does that happen automatically.

My program is supposed to take a list of eight files, halve them until there are only two files, merge and sort these files and return the parent thread to merge and sort the files until all eight have been processed.

Perhaps someone could give tell me if my approach is wrong? I would be very grateful.

Thanks :)
flldom

---

