---
title: "question about phread.h"
date: 2011-05-29
forum: General Help
---

### Post by alex_goacross on 2011-05-29
Hi!I'm a green hand at ubuntu programming! I don't know whether it is the right category to post.:)
Here is my problem.

--------------------------
#include <pthread.h>


void* thr_fun(void*)
{
    printf("thr_fun");
}

pthread_t ntid;
int err;
...
err = pthread_create(&ntid, NULL, thr_fun, NULL);
...
--------------------------

I got the compile message:
***threadtest.c:15: undefined reference to `pthread_create***'

at first, I checked the phread.h file under CMD:
$:locate pthread.h
/usr/include/pthread.h

so, I think this head file does exist in my disk.
But I got the message again.


Thanks for any reply.
Alex

---

### Post by katykat on 2011-05-29
Ubuntu does not seem to too friendly to compiling. You may need to manually set include paths, as well as make sure you have all the necessary compiler packages from Synaptic.

As Ubuntu deviates more and more away from traditional Linux and its path structure, compiling can get  more and more hairy.....

Havent seen anything here on DIY kernels....

---

### Post by alex_goacross on 2011-05-29
> **katykat said:**
> Ubuntu does not seem to too friendly to compiling. You may need to manually set include paths, as well as make sure you have all the necessary compiler packages from Synaptic.

As Ubuntu deviates more and more away from traditional Linux and its path structure, compiling can get  more and more hairy.....

Havent seen anything here on DIY kernels....

Thanks for your advice!
Seeks like I have lot of works to do on my own!

Message was edited by alex at 15:18 pm on 05/29/11.

---

### Post by alex_goacross on 2011-05-30
I fixed my problem!
Using the -lpthread option to compile and do noting configuration.
-----------------------
gcc myFun.c -o myFun -lpthread
-----------------------

Message was edited by alex at 10:43 on 05/30/11.

---

