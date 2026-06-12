---
title: "copy_from_user does not copy from process-heap"
date: 2009-08-16
forum: General Help
---

### Post by najoshi on 2009-08-16
Hello all,
I need a positive reply from you.
I want to copy the user-process-heap to the kernel space memory.
For that, I wrote the following code but it does not copy.
---------------- code --------------
unsigned long length_of_heap_vma = < length of vma pointing to process-heap > ;
void * kernel_mem = (void *) kmalloc(length_of_heap_vma,GFP_KERNEL);
unsigned long bytes_not_copied = 0;
 
bytes_not_copied = copy_from_user(kernel_mem,(void *)vm->vma_start,length_of_heap_vma);//vm points to process heap
printk("failed to copy %ld bytes.",bytes_not_copied); //it always displays a non-zero value.
---------------- end of code --------
 
now the PROBLEM is that - the code successfuly compiles, but when I execute it, it copies not a single byte and
bytes_not-copied always becomes equal to length_of_heap_vma. No compile-time or execution-time error occurs.
(note: my process has the following dynamic memory in user-part:
int * p = (int*) malloc(5 * sizeof(int));
for(i=0;i<5;i++)
p[i]= i;
)

---

### Post by dcstar on 2009-08-16
> **najoshi said:**
> Hello all,
I need a positive reply from you.
I want to copy the user-process-heap to the kernel space memory.
For that, I wrote the following code but it does not copy.
---------------- code --------------
unsigned long length_of_heap_vma = < length of vma pointing to process-heap > ;
void * kernel_mem = (void *) kmalloc(length_of_heap_vma,GFP_KERNEL);
unsigned long bytes_not_copied = 0;
 
bytes_not_copied = copy_from_user(kernel_mem,(void *)vm->vma_start,length_of_heap_vma);//vm points to process heap
printk("failed to copy %ld bytes.",bytes_not_copied); //it always displays a non-zero value.
---------------- end of code --------
 
now the PROBLEM is that - the code successfuly compiles, but when I execute it, it copies not a single byte and
bytes_not-copied always becomes equal to length_of_heap_vma. No compile-time or execution-time error occurs.
(note: my process has the following dynamic memory in user-part:
int * p = (int*) malloc(5 * sizeof(int));
for(i=0;i<5;i++)
p[i]= i;
)

This is **not** a programming forum, it is a General support forum.

---

