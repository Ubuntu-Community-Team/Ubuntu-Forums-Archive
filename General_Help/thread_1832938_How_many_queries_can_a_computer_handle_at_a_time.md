---
title: "How many queries can a computer handle at a time?"
date: 2011-08-25
forum: General Help
---

### Post by Drazer on 2011-08-25
I have heard that a computer can handle only 1 querie at a time.....
If its true the what is use of such advance Hex-core or Quad-core processor....????
And what abt Multitasking?????
:mad:

---

### Post by seawolf167 on 2011-08-25
Linux uses processes and limits the number of concurrent processes that can be running by a single user. You can see this limit by typing the below command into a terminal.

```
cat /proc/sys/kernel/threads-max
```

---

### Post by haqking on 2011-08-25
remember that threads and processes are different.

A process can have multiple threads.

A thread is an entity within a process which can be scheduled for execution.

---

### Post by The Cog on 2011-08-25
A single processor computer can only be actively executing instructions from one program at any instant in time. But of course it can switch between programs very quickly, so that all programs appear to be running at the same time. 

And just one program can be handling multiple queries at any one time, probably again by switching rapidly between queries, doing a bit of each at a time.

So in practical terms, a computer can be handling many thousands of queries all at the same time.

---

### Post by Megaptera on 2011-08-25
Mine ... with me at the keyboard?? Less than one :(

---

