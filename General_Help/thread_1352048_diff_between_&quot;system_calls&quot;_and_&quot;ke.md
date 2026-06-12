---
title: "diff between &quot;system calls&quot; and &quot;kernel threads&quot;"
date: 2009-12-11
forum: General Help
---

### Post by shariefbe on 2009-12-11
Hello,
  May i know what is the difference between systems calls and kernel threads. I googled for the answer but as a newbie i didnt get understand what the difference?

---

### Post by kjohri on 2009-12-11
System calls are the functions that are done by the Linux kernel to provide services like process management, memory management, filesystem management and I/O. For example, if you want to write on a file, "write" system call has to be used. 

A process is a program under execution. A process may have multiple parallel (kernel) threads of execution. You need to call the pthread_create system call to create a thread.

For excellent coverage of this subject refer to the book, "Advanced Unix Programming", Second Edition by Marc J. Rochkind (Addison-Wesley).

---

