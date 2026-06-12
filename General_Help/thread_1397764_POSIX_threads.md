---
title: "POSIX threads"
date: 2010-02-03
forum: General Help
---

### Post by cybo on 2010-02-03
i'm trying to understand the POSIX threads and i can't understand when does the thread start: does it start when i do

pthread_create() 
or when i do
pthread_join()
or maybe i'm missing something.

i do understand that pthread_join() causes the calling thread to wait till the called thread is finished.

can anybody clarify?

---

### Post by lloyd_b on 2010-02-03
> **cybo said:**
> i'm trying to understand the POSIX threads and i can't understand when does the thread start: does it start when i do

pthread_create() 
or when i do
pthread_join()
or maybe i'm missing something.

i do understand that pthread_join() causes the calling thread to wait till the called thread is finished.

can anybody clarify?

The thread is created and starts running when you run pthread_create().  pthread_join() is simply a way to wait for the other thread to complete before continuing the current thread (and allows the joining thread to see the exit status, if any, of the joined thread).

Lloyd B.

P.S. For future reference, I'd suggest posting questions like this in the Programming section rather than General - you're more likely to get a good answer quickly there.

---

### Post by cybo on 2010-02-04
lloyd_b, thanks it helped.

---

